---
title: Pdostatement::errorcode |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4161abec-c12b-444e-9de5-f1dac7b3e0e4
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dd3c5de96f06a7cbf705702f87d460cd2aa7c88
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="pdostatementerrorcode"></a>PDOStatement::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

データベース ステートメント オブジェクトの最新の操作の SQLSTATE を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
string PDOStatement::errorCode();  
```  
  
## <a name="return-value"></a>戻り値  
5 文字の SQLSTATE を文字列として返すか、ステートメント ハンドルに操作がない場合は、NULL が返されます。  
  
## <a name="remarks"></a>解説  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
次の例では、エラーが発生している SQL クエリを示します。  さらに、エラー コードを示します。  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print $stmt->errorCode();  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
