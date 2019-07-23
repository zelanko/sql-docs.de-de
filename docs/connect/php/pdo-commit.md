---
title: 'PDO:: Commit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 41a87a6444ce61af5b2b8a00aa61306dd90d0d8c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993289"
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
  
## <a name="remarks"></a>Remarks  
PDO::commit ist nicht betroffen von dem Wert des PDO::ATTR_AUTOCOMMIT (und hat keinen Einfluss auf diesen).  
  
Ein Beispiel, das PDO::commit verwendet, finden Sie unter [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) .  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
