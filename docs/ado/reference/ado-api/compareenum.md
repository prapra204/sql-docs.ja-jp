---
title: CompareEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CompareEnum
helpviewer_keywords:
- CompareEnum enumeration [ADO]
ms.assetid: bc8f710d-0621-4673-8d8e-0361e44abed0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16bc257e151fc68eddd9268c10cf9d093d9c8491
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="compareenum"></a>CompareEnum
ブックマークによって表される 2 つのレコードの相対位置を指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adCompareEqual**|1|ブックマークが等しいことを示します。|  
|**adCompareGreaterThan**|2|最初のブックマークが、2 つ目の後にあることを示します。|  
|**adCompareLessThan**|0|2 つ目の最初のブックマークであることを示します。|  
|**adCompareNotComparable**|4|ブックマークを比較できないことを示します。|  
|**adCompareNotEqual**|3|ブックマークが異なっており、順位がないことを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.Compare.EQUAL|  
|AdoEnums.Compare.GREATERTHAN|  
|AdoEnums.Compare.LESSTHAN|  
|AdoEnums.Compare.NOTCOMPARABLE|  
|AdoEnums.Compare.NOTEQUAL|  
  
## <a name="applies-to"></a>適用対象  
 [CompareBookmarks メソッド (ADO)](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)  
  
## <a name="see-also"></a>参照  
 [CompareBookmarks メソッド (ADO)](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)
