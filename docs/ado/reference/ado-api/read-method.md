---
title: Read メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords:
- Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 53e3f6c3b780d9d78697fb33dfea5574457a6b2c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="read-method"></a>Read メソッド
バイナリから指定したバイト数を読み取ります[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *NumBytes*  
 省略可。 A**長い**ファイルから読み取るバイト数を指定する値または[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)値**adReadAll**、既定値です。  
  
## <a name="return-value"></a>戻り値  
 **読み取り**メソッドは、指定したバイト数またはからストリーム全体を読み取ります、**ストリーム**オブジェクトし、結果として得られるデータとして返します、**バリアント**です。  
  
## <a name="remarks"></a>解説  
 場合*NumBytes*はバイト数よりも多いのままに、**ストリーム**、残っているバイト数のみが返されます。 指定された長さに合わせて読み取られるデータが埋め込まれていません*NumBytes*です。 読み取るデータがない場合は、値が null のバリアント型が返されます。 **読み取り**旧バージョンと読み取りに使用することはできません。  
  
> [!NOTE]
>  *NumBytes*常にバイトを測定します。 テキストの**ストリーム**オブジェクト ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)、使用して[ReadText](../../../ado/reference/ado-api/readtext-method.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ReadText メソッド](../../../ado/reference/ado-api/readtext-method.md)
