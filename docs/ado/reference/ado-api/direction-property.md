---
title: "方向プロパティ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::Direction
helpviewer_keywords:
- Direction property
ms.assetid: d5732578-3434-4dcd-a9f7-db1abd1b3b94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a81c60a4505e1c5e420583c474109d0d08f4fb6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="direction-property"></a>方向プロパティ
示すかどうか、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)入力パラメーター、出力パラメーター、入力と出力パラメーターを表しますパラメーターがストアド プロシージャからの戻り値の場合またはします。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、[値](../../../ado/reference/ado-api/parameterdirectionenum.md)値。  
  
## <a name="remarks"></a>解説  
 使用して、**方向**プロパティに、またはプロシージャからパラメーターを渡す方法を指定します。 **方向**読み取り/書き込みプロパティです。 これにより、この情報を返すしないプロバイダーと連携するか、ADO プロバイダーに、パラメーター情報を取得するの余分な呼び出しを行う必要がない場合は、この情報を設定します。  
  
 すべてのプロバイダーは、ストアド プロシージャのパラメーターの方向を決定できます。 このような場合は、設定する必要があります、**方向**プロパティ クエリを実行する前にします。  
  
## <a name="applies-to"></a>適用対象  
 [パラメーター オブジェクト](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの使用例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
