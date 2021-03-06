---
title: IIF (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IIF_TSQL
- IIF
dev_langs:
- TSQL
helpviewer_keywords:
- IIF function
ms.assetid: e3ccf8ed-1cec-43ac-90b7-d8597c24b050
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: be47b84edfd15c0c175062972634c06044dd109c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="logical-functions---iif-transact-sql"></a>論理関数 - IIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではブール式が true または false のいずれに評価されるかによって、2 つの値のいずれかを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
IIF ( boolean_expression, true_value, false_value )  
```  
  
## <a name="arguments"></a>引数  
 *boolean_expression*  
 有効なブール式です。  
  
 この引数がブール式でない場合、構文エラーが発生します。  
  
 *true_value*  
 *boolean_expression* が true に評価された場合に返す値。  
  
 *false_value*  
 *boolean_expression* が false に評価された場合に返す値。  
  
## <a name="return-types"></a>戻り値の型  
 内の型からの優先順位が最も高いデータ型を返します *true_value* と *false_value*です。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 IIF は CASE 式を簡略化して書き込みます。 最初の引数として渡されたブール式を評価し、評価の結果に基づいて他の 2 つの引数のいずれかを返します。 つまり、 *true_value* ブール式が true の場合、返されると、 *false_value* ブール式が false または不明のかどうかに返されます。 任意の型の *true_value* と *false_value* を指定できます。 ブール式、NULL 処理、および戻り値の型に対する CASE 式に適用されるのと同じ規則が IIF にも適用されます。 詳細については、を参照してください。 [場合 (&) #40 です。TRANSACT-SQL と #41;](../../t-sql/language-elements/case-transact-sql.md).  
  
 IIF が CASE に変換されるという事実は、この関数の動作の他の側面にも影響を与えます。 CASE 式では最大 10 のレベルまで入れ子が許容されるため、IIF ステートメントでも最大 10 のレベルまで入れ子が許容されます。 また、IIF は、意味が同じ CASE 式として他のサーバーにリモート処理を行い、リモート処理された CASE 式のすべての動作を実行します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-iif-example"></a>A. 簡単な IIF の例  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a > @b, 'TRUE', 'FALSE' ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------  
TRUE  
  
(1 row(s) affected)  
```  
  
### <a name="b-iif-with-null-constants"></a>B. NULL 定数を使用する IIF  
  
```  
SELECT IIF ( 45 > 30, NULL, NULL ) AS Result;  
```  
  
 このステートメントの結果はエラーになります。  
  
### <a name="c-iif-with-null-parameters"></a>C. NULL パラメーターを使用する IIF  
  
```  
DECLARE @P INT = NULL, @S INT = NULL;  
SELECT IIF ( 45 > 30, @p, @s ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------  
NULL  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [選択 (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/logical-functions-choose-transact-sql.md)  
  
  
