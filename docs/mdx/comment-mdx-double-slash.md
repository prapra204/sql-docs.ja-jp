---
title: //(コメント)(MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6570694bc38eb6f32f660006f1ed1b6797793b7b
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739521"
---
# <a name="comment-mdx-double-slash"></a>コメントの MDX 二重スラッシュ


  ユーザーが入力したテキストを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>コメント  
 コメントは、別個の行として挿入することも、多次元式 (MDX) スクリプトの行の末尾で入れ子にすることも、MDX ステートメント内で入れ子にすることも可能です。 サーバーはコメントを評価しません。  
  
 単一行のみのコメントには、// を使用します。 // を使用して挿入するコメントは、改行文字で区切ります。  
  
 コメントの長さには制限がありません。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
```  
// This member returns the gross profit margin for product types  
// and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM // Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>参照  
 [コメント &#40;MDX&#41;](../mdx/comment-mdx.md)   
 [-- &#40;コメント&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md)   
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
