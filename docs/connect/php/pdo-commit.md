---
title: PDO::commit
description: API-Referenz für die PDO::commit-Funktion im Microsoft PDO_SQLSRV-Treiber für PHP für SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94e42cb5fccba7d69025de85b0247f7a4c065c03
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646190"
---
# <a name="pdocommit"></a>PDO::commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Sendet Befehle an die Datenbank, die nach dem Aufruf von [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) ausgegeben wurden und setzt die Verbindung in den Autocommit-Modus zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
bool PDO::commit();  
```  
  
## <a name="return-value"></a>Rückgabewert  
„true“, bei erfolgreichem Aufruf der Methode; andernfalls „false“.  
  
## <a name="remarks"></a>Bemerkungen  
PDO::commit ist nicht betroffen von dem Wert des PDO::ATTR_AUTOCOMMIT (und hat keinen Einfluss auf diesen).  
  
Ein Beispiel, das PDO::commit verwendet, finden Sie unter [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) .  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
