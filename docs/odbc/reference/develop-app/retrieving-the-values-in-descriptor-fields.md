---
title: 記述子フィールドの値を取得する |Microsoft ドキュメント
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8284167a27439c65256ee4559210843ec7dcffe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911387"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>記述子フィールドの値を取得します。
アプリケーションが呼び出すことができます**SQLGetDescField**を記述子レコードの 1 つのフィールドを取得します。 **Sqlgetdescfield による**ODBC では、定義されたすべての記述子フィールドとドライバーの定義済みのフィールドも、アプリケーションにアクセスします。  
  
 **SQLGetDescRec**列またはパラメーターのデータのストレージとデータ型に影響する複数の記述子フィールドの設定を取得すると呼ばれることができます。
