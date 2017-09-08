---
title: "@@VERSION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@VERSION'
- '@@VERSION_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@VERSION function'
- current SQL Server installation information
- versions [SQL Server], @@VERSION
- processors [SQL Server], types
ms.assetid: 385ba80e-7c28-41a5-9cdb-5648f3785983
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b8367bb24a37996b2956e3107113812a32086fed
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="version---transact-sql-configuration-functions"></a>バージョン - Transact SQL 構成関数
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のインストールのシステムとビルドの情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
@@VERSION  
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar**  
  
## <a name="remarks"></a>解説  
 @@VERSION結果は 1 つの nvarchar 文字列として表示されます。 使用することができます、 [SERVERPROPERTY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/serverproperty-transact-sql.md)個々 のプロパティ値を取得します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、次の情報が返されます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン  
  
-   プロセッサ アーキテクチャ  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のビルド日  
  
-   著作権表記  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エディション  
  
-   オペレーティング システムのバージョン  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]では、次の情報が返されます。  
  
-   エディション - "Windows Azure SQL データベース"  
  
-   製品レベル - "(CTP)" または "(RTM)"  
  
-   製品バージョン  
  
-   ビルド日  
  
-   著作権表記  
  
## <a name="examples"></a>使用例  
  
### <a name="a-return-the-current-version-of-includessnoversionincludesssnoversion-mdmd"></a>A: の現在のバージョンを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 次の例では、現在のインストールに関するバージョン情報を返します。  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-includessdwincludesssdw-mdmd"></a>B. 現在のバージョンを返す[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>参照  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  

