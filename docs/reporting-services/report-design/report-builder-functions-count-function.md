---
title: Count 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7b50b101-daf8-4fb0-ae04-57384755779f
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2016b2aef554c2efa6c97b8541607bacd77e23fd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33025149"
---
# <a name="report-builder-functions---count-function"></a>レポート ビルダー関数 - Count 関数
  式で指定された NULL 以外の値の数を、指定されたスコープのコンテキストで評価して返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
Count(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *式 (expression)*  
 (**Variant** または **Binary**) この集計関数の実行対象の式です ( `=Fields!FieldName.Value`など)。  
  
 *スコープ (scope)*  
 (**String**) 集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。 *scope* を指定しない場合、現在のスコープが使用されます。  
  
 *再帰*  
 (**列挙型**) 省略可。 **Simple** (既定値) または **RdlRecursive**です。 集計を再帰的に実行するかどうかを指定します。  
  
## <a name="return-type"></a>戻り値の型  
 **Integer**値を返します。  
  
## <a name="remarks"></a>Remarks  
 *scope* の値は文字列定数である必要があり、式にすることはできません。 外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。 集計の集計では、入れ子になった集計に、子のスコープを指定できます。  
  
 *Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。  
  
-   入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。 式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。  
  
-   入れ子集計の*Scope* には、データセット名は使用できません。  
  
-   *Expression* には、 **First**、 **Last**、 **Previous**、または **RunningValue** の各関数を含めることができません。  
  
-   *Expression* には、 *recursive*を指定する入れ子集計を含めることができません。  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
 再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。  
  
 例  
  
## <a name="description"></a>Description  
 次のコード例では、既定のスコープおよび親グループのスコープで、 `Size` の NULL でない値の数を計算する式を示します。 この式は、子グループ `GroupbySubcategory`に属する行内のセルに追加されます。 親グループは `GroupbyCategory`です。 この式では、 `GroupbySubcategory` (既定のスコープ) の結果、次に `GroupbyCategory` (親グループのスコープ) の結果が表示されます。  
  
> [!NOTE]  
>  実際には、式に復帰および改行を含めないでください。サンプル コードでは、ドキュメントを読みやすくするためにこれらが含まれています。 次の例をコピーする場合は、各行の復帰を削除してください。  
  
## <a name="code"></a>コード  
  
```  
="Count (Subcategory): " & Count(Fields!Size.Value) &   
"Count (Category): " & Count(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a>参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
