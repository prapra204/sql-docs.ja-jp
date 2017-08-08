---
title: "DB2 への接続 (DB2ToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9d485fd0-ab5d-402a-a59a-e9982a61b7de
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 733fae47c5c74eb120b7f8719dd53675eb5b7e36
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="connect-to-db2-db2tosql"></a>DB2 への接続 (DB2ToSQL)
使用して、 **DB2 への接続**を移行する DB2 データベースに接続する ダイアログ ボックス。  
  
このダイアログ ボックスにアクセスする、**ファイル**メニューの  **DB2 への接続**です。 以前接続した場合、コマンドは**DB2 への再接続**です。  
  
## <a name="options"></a>オプション  
**プロバイダー**  
DB2 データベースへの接続用のデータ アクセス プロバイダーを選択します。 使用可能なプロバイダーは、DB2 クライアント プロバイダー、OLE DB プロバイダーです。 既定値は、DB2 クライアント プロバイダーです。  
  
**モード**  
標準、TNSNAME、または接続文字列のいずれかのモードを選択します。  
  
-   標準モードでは、入力またはプロバイダー、サーバー名、サーバーのポート、DB2 SID、ユーザー名とパスワードの値を選択します。  
  
-   TNSNAME モードでは、DB2 データベース、ユーザー名とパスワードの接続識別子 (TNS 別名) を入力します。  
  
-   接続文字列のモードでは、接続文字列を指定します。  
  
    > [!IMPORTANT]  
    > テキストは、パスワードを含める場合があり、クリア テキストとして送信されるため、接続文字列のモードを使用することはお勧めしません。  
  
既定値は、標準モードです。  
  
**サーバー名**  
DB2 サーバー名を入力します。 既定のサーバー名は、コンピューター名と同じです。 標準モードのオプションです。  
  
**[サーバー ポート]**  
DB2 への接続を 1521 (既定値) 以外のポート番号を使用している場合は、ポート番号を入力します。 標準モードのオプションです。  
  
**識別子を接続します。**  
DB2 の入力の識別子を接続します。 これは、ローカル tnsnames.ora ファイルで定義されているデータベースのエイリアスです。  
  
TNSNAME モード オプションです。  
  
**DB2 SID**  
データベースの SID を入力します。 SID は、コンピューター上の DB2 データベースを区別する識別子です。 データベースの既定で SID は、データベース名の最初の 8 文字です。  
  
標準モードのオプションです。  
  
**ユーザー名**  
SSMA が DB2 データベースへの接続に使用するユーザー名を入力します。  
  
**Password**  
ユーザー名に対応するパスワードを入力します。  
  
**[接続文字列]**  
> [!IMPORTANT]  
> テキストは、パスワードを含める場合があり、クリア テキストとして送信されるため、接続文字列のモードを使用することはお勧めしません。  
  
接続文字列のモードを使用する場合は、DB2 に接続の完全な接続文字列を入力します。  
  
接続文字列は、パラメーターの名前と値のペアで構成されます。  
  
-   OLE DB 接続文字列については、次を参照してください。 [Microsoft OLE DB Provider for DB2](http://go.microsoft.com/fwlink/?LinkId=85640) 、MSDN ライブラリの記事です。  
  
SSMA 接続文字列の場合に、プロバイダーのパラメーターを必ず含めます。 また、DB2 に接続するときに、ポート パラメーターを含めることを確認します。  
  
