---
title: 表示オブジェクト (ADOX) |Microsoft ドキュメント
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
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a55d77b7bb7f79ee5871445d5169a4dfd2de5f5d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="view-object-adox"></a>ビュー オブジェクト (ADOX)
フィルター選択された一連のレコードまたは仮想テーブルを表します。 ADO と組み合わせて使用すると[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト、**ビュー**オブジェクトは追加、削除、または変更、ビューを使用できます。  
  
## <a name="remarks"></a>解説  
 ビューは、他のデータベース テーブルまたはビューから作成された、仮想テーブルです。 **ビュー**オブジェクトでは、理解、またはプロバイダーの"CREATE VIEW"構文を使用することがなく、ビューを作成することができます。  
  
 プロパティを持つ、**ビュー**オブジェクトをすることができます。  
  
-   ビューを識別、[名前](../../../ado/reference/adox-api/name-property-adox.md)プロパティです。  
  
-   ADO の指定**コマンド**を追加、削除、またはビューを変更するために使用できるオブジェクト、[コマンド](../../../ado/reference/adox-api/command-property-adox.md)プロパティです。  
  
-   日付情報を返す、 [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md)と[DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md)プロパティです。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [View オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [ビューとフィールド コレクションの例 (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [ビューの追加メソッドの例 (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [ビューのコレクション、CommandText プロパティの例 (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [ビューの削除の方法の例 (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
