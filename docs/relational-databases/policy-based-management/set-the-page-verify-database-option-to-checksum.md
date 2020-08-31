---
title: Festlegen der PAGE_VERIFY-Datenbankoption auf CHECKSUM | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie überprüfen, ob CHECKSUM für die Option PAGE_VERIFY festgelegt ist, wodurch gesteuert wird, ob SQL Server-Datenbank-Engine eine Prüfsumme berechnet, um die Bereitstellung der Integrität von Datendateien zu unterstützen.
ms.custom: ''
ms.date: 08/19/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4dda2b9138882490b1556b9dbb39f71e35767f5f
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646510"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a>Festlegen der PAGE_VERIFY-Datenbankoption auf CHECKSUM
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel überprüft, ob die PAGE_VERIFY-Datenbankoption auf CHECKSUM festgelegt ist. Wenn CHECKSUM für die PAGE_VERIFY-Datenbankoption angegeben wird, berechnet [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] beim Schreiben der Seite auf den Datenträger eine Prüfsumme des Inhalts der gesamten Seite und speichert den Wert im Seitenkopf. Wenn die Seite vom Datenträger gelesen wird, wird die Prüfsumme erneut berechnet und mit dem im Seitenkopf gespeicherten Prüfsummenwert verglichen. Dadurch wird ein hohes Maß an Integrität der Datendateien bereitgestellt.  Wenn Sie die Option PAGE VERIFY CHECKSUM für eine Datenbank verwenden und SQL Server erkennt, dass eine Seite geändert wurde, nachdem sie auf den Datenträger geschrieben wurde, gibt SQL Server [Msg 824](../errors-events/mssqlserver-824-database-engine-error.md) aus, nachdem die Seite wieder auf dem Datenträger gelesen wurde. 
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die PAGE_VERIFY-Datenbankoption auf CHECKSUM fest. Die Verwendung der Datenbankoption PAGE_VERIFY CHECKSUM bietet die stabilste Erkennung von Datenbankkonsistenzproblemen, die vom E/A-Pfad des Systems verursacht werden.
  
## <a name="for-more-information"></a>Weitere Informationen  
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
