---
title: CancelBatch メソッド (ADO) |Microsoft ドキュメント
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
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 241bf36ab3ee4babf8d4e306b9d27a350985cb20
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="cancelbatch-method-ado"></a>CancelBatch メソッド (ADO)
保留中のバッチ更新をキャンセルします。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>パラメーター  
 *AffectRecords*  
 省略可。 [AffectEnum](../../../ado/reference/ado-api/affectenum.md)レコードの数を示す値、 **CancelBatch**メソッドに影響します。  
  
## <a name="remarks"></a>解説  
 使用して、 **CancelBatch**保留中の更新プログラムをキャンセルする方法、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)バッチ更新モードでします。 場合、**レコード セット**即時更新モードでは、呼び出す**CancelBatch**せず**adAffectCurrent**でエラーが生成されます。  
  
 現在のレコードを編集するかを呼び出すときに、新しいレコードを追加することは**CancelBatch**、ADO を最初に呼び出す、[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)をキャンセルするメソッドは、変更をキャッシュします。 その後、保留中のすべての変更、 **Recordset**はすべて取り消されます。  
  
 現在のレコードが確定後にない可能性があります、 **CancelBatch**呼び出すには、新しいレコードを追加する処理を行っていた場合に特にです。 このため、お勧めの既知の場所に、現在のレコードの位置を設定する、 **Recordset**後、 **CancelBatch**呼び出します。 たとえば、呼び出し、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッドです。  
  
 保留中の更新をキャンセルしようとすると、失敗した場合 (たとえば、レコードが別のユーザーによって削除されている場合) の基になるデータの競合があるため、プロバイダーは、警告を返します、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションは停止されませんが、プログラムの実行。 要求されたすべてのレコードの競合がある場合にのみ、実行時エラーが発生します。 使用して、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティ (**adFilterAffectedRecords**) および[ステータス](../../../ado/reference/ado-api/status-property-ado-recordset.md)競合しているレコードを検索するプロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [UpdateBatch と CancelBatch メソッドの例 (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch と CancelBatch メソッドの例 (vc++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Cancel メソッド (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [ただしメソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [ただしメソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)
