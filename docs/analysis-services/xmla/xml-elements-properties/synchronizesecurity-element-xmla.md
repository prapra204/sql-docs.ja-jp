---
title: SynchronizeSecurity 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f99f4c0ddf212d2fac33abd08c33ccf3dbe7998
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576484"
---
# <a name="synchronizesecurity-element-xmla"></a>SynchronizeSecurity 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  中に、ロールや権限などのセキュリティ定義を同期する方法を指定、[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*skipMembership*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **セキュリティ**要素は、実行時に役割と、Analysis Services データベースで定義された権限など、セキュリティ定義を同期するかどうかを決定する**同期**コマンド。 この要素が Windows ユーザー アカウントと、セキュリティ定義のメンバーとして定義されているグループがの一部として含まれるかどうかを決定しても、**同期**コマンド。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*skipMembership*|セキュリティの定義が含まれますが、中に、メンバーシップ情報を除外する**同期**コマンド。|  
|*CopyAll*|セキュリティの定義と中にメンバーシップ情報が含まれて、**同期**コマンド。|  
|*IgnoreSecurity*|実行時にセキュリティ定義を除外する、**同期**コマンド。|  
  
## <a name="see-also"></a>参照
 [セキュリティ要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
