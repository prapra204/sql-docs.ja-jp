---
title: "CEILING (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CEILING_TSQL
- CEILING
dev_langs:
- TSQL
helpviewer_keywords:
- smallest integer great than or equal to expression
- integers [SQL Server]
- CEILING function [Transact-SQL]
ms.assetid: e736b43a-9457-4781-95a4-4bcf9d4fc46a
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c8b61f59733fa0696e8176f6c380139330c575e9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="ceiling-transact-sql"></a>CEILING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

指定された数値式以上の整数のうち最小のものを返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
CEILING ( numeric_expression )  
```  
  
## <a name="arguments"></a>引数  
*numeric_expression*  
[式](../../t-sql/language-elements/expressions-transact-sql.md)の正確な型または概数の数値データのカテゴリを除く入力、**ビット**データ型。
  
## <a name="return-types"></a>戻り値の型
*numeric_expression*と同じ型を返します。
  
## <a name="examples"></a>使用例  
次の例では、正の数値、負の数値、および 0 を使った CEILING 関数を示します。
  
```sql
SELECT CEILING($123.45), CEILING($-123.45), CEILING($0.0);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
--------- --------- -------------------------   
124.00    -123.00    0.00                       
  
(1 row(s) affected)  
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]そして[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

次の例では、正の数値、負の値の使用およびゼロ値を使った CEILING 関数を示します。
  
```sql
SELECT CEILING(123.45), CEILING(-123.45), CEILING(0.0);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`------- --------- --------`
  
`124.00  -123.00   0.00`
  
## <a name="see-also"></a>参照
[システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  
