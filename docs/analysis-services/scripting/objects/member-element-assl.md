---
title: Member 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a266e1c3524a489f1f75cf6675dc8a9b4677d9a9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037163"
---
# <a name="member-element-assl"></a>Member 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メンバーの名前を含む、[グループ](../../../analysis-services/scripting/objects/group-element-assl.md)要素であるかの[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Members>  
   <Member>  
      <Name>...</Name>  
   </Member>  
</Members>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メンバー](../../../analysis-services/scripting/collections/members-element-assl.md)|  
|子要素|[名前](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**メンバー**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Group>と<xref:Microsoft.AnalysisServices.Role>です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
