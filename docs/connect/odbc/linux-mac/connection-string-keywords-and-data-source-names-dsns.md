---
title: SQL Server への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f49c0105f96f446c627f5ec1b5f47ee62b28558
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852507"
---
# <a name="connecting-to-sql-server"></a>SQL Server への接続
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

このトピックへの接続を作成する方法について説明します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="connection-properties"></a>接続プロパティ  

参照してください[DSN と接続文字列キーワード、および属性](../../../connect/odbc/dsn-connection-string-attribute.md)すべての接続文字列キーワードと Linux、Mac でサポートされる属性

> [!IMPORTANT]  
> データベース ミラーリングを使用する (フェールオーバー パートナーがある) データベースに接続する場合は、接続文字列にデータベース名を指定しないでください。 代わりに、送信、**使用** *database_name*クエリを実行する前に、データベースに接続するコマンド。  
  
渡された値、**ドライバー**キーワードは、次のいずれかを指定できます。  
  
-   ドライバーをインストールしたときに使用した名前。

-   ドライバーをインストールするために使用するテンプレート .ini ファイルで指定されているドライバー ライブラリへのパス。  

DSN を作成する (必要な場合) を作成し、ファイルを編集して **~/.odbc.ini** (`.odbc.ini` 、ホーム ディレクトリ)、現在のユーザーにのみアクセスできるユーザー DSN のまたは`/etc/odbc.ini`のシステム DSN (管理のために必要な権限です)。DSN の最低限必要なエントリを表示するサンプル ファイルを次に示します。  

```  
[MSSQLTest]  
Driver = ODBC Driver 13 for SQL Server  
Server = [protocol:]server[,port]  
#   
# Note:  
# Port is not a valid keyword in the odbc.ini file  
# for the Microsoft ODBC driver on Linux or macOS
#  
```  

サーバーに接続するために、必要に応じてプロトコルとポートを指定することができます。 たとえば、 **Server = tcp:***servername***、12345**です。 Linux および macOS ドライバーでサポートされる唯一のプロトコルは`tcp`します。

静的なポートの名前付きインスタンスに接続するには、使用<b>サーバー =</b>*servername*、**port_number**です。 動的ポートに接続することはサポートされていません。  

テンプレート ファイル DSN 情報を追加しに追加するには、次のコマンドを実行する代わりに、 `~/.odbc.ini` :
 - **odbcinst -i -s -f** *template_file*  
 
使用して、ドライバーが動作していることを確認することができます`isql`このコマンドを使用するか、接続をテストします。
 - **OutFile.dat-s out、bcp master.INFORMATION_SCHEMA.TABLES <server> -u <name> ~ P <password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Secure Sockets Layer (SSL) を使用する  
Secure Sockets Layer (SSL) を使用するには接続を暗号化する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 SSL 保護[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]ユーザー名とネットワーク経由でのパスワード。 また、サーバーの ID を検証して、man-in-the-middle (MITM) 攻撃に対して保護することもできます。  

暗号化を有効にすると、セキュリティは向上しますが、パフォーマンスは低下します。

詳細については、次を参照してください。 [SQL Server への接続の暗号化](http://go.microsoft.com/fwlink/?LinkId=220900)と[を使用して検証を伴わない暗号化](https://docs.microsoft.com/en-us/sql/relational-databases/native-client/features/using-encryption-without-validation)です。

**Encrypt** と **TrustServerCertificate**の設定に関係なく、サーバー ログインの資格情報 (ユーザー名とパスワード) は常に暗号化されます。 次の表は、 **Encrypt** 設定と **TrustServerCertificate** 設定の効果の一覧です。  

||**TrustServerCertificate=no**|**TrustServerCertificate = [はい]**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されません。|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されません。|  
|**暗号化 = [はい]**|サーバー証明書は確認されます。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されます。<br /><br />サブジェクト共通名 (CN) またはサブジェクトの別名 (SAN) 内で名前 (または IP アドレス)、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL 証明書は、サーバー名 (または IP アドレス)、接続文字列で指定されたと一致します。|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されます。|  

既定では、暗号化された接続はサーバーの証明書を必ず検証します。 ただし、自己署名証明書を持つサーバーに接続する場合も追加、`TrustServerCertificate`信頼された証明機関の一覧に対して証明書の確認をバイパスするにはオプション。  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL は、OpenSSL ライブラリを使用します。 次の表は、OpenSSL の最低限のサポートされるバージョンと、各プラットフォームの既定の証明書信頼ストアを示します。

|プラットフォーム|最低限の OpenSSL のバージョン|既定の証明書信頼ストアの場所|  
|------------|---------------------------|--------------------------------------------|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71 |1.0.1|/etc/ssl/certs|
|macOS 10.13|1.0.2|/usr/local/etc/openssl/certs|
|macOS 10.12|1.0.2|/usr/local/etc/openssl/certs|
|OS X 10.11|1.0.2|/usr/local/etc/openssl/certs|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 12 |1.0.1|/etc/ssl/certs|
|SuSE Linux Enterprise 11 |0.9.8|/etc/ssl/certs|
|Ubuntu 17.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.04 |1.0.2|/etc/ssl/certs|
  
接続文字列を使用して、暗号化を指定することも、`Encrypt`オプションを使用する場合**SQLDriverConnect**に接続します。

## <a name="see-also"></a>参照  
[Linux および macOS 上の SQL Server 用 Microsoft ODBC Driver をインストールします。](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)
