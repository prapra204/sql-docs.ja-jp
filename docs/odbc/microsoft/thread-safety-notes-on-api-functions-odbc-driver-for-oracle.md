---
title: API 関数 (ODBC Driver for Oracle) にスレッド セーフの注意事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af91cf6ea125feaa814030c9eb462a096bbcd2e2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905634"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>API 関数 (ODBC Driver for Oracle) にスレッド セーフの注意事項
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Microsoft ODBC Driver for Oracle はスレッド セーフです。ただし、Oracle では、単一の接続で複数の同時実行ステートメントは使用はできません。 ドライバーは、この制限を強制します。 つまり、マルチ スレッド アプリケーションで、任意のスレッドがいつでも for Oracle ODBC ドライバーに呼び出すことができますが、ドライバー ブロックが同じ接続で、ドライバーから他のスレッド、元のスレッドが、ドライバーを離れるまでします。  
  
 ドライバーは、次の 2 つの異なる接続で 2 つのステートメントがある場合にブロックされません。 ただし、2 つのステートメントで 1 つの接続がある場合はブロックが発生する可能性です。
