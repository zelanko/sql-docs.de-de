---
title: Festlegen der PAGE_VERIFY-Datenbankoption auf CHECKSUM | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie überprüfen, ob CHECKSUM für die Option PAGE_VERIFY festgelegt ist, wodurch gesteuert wird, ob SQL Server-Datenbank-Engine eine Prüfsumme berechnet, um die Bereitstellung der Integrität von Datendateien zu unterstützen.
ms.custom: ''
ms.date: 03/04/2017
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
ms.openlocfilehash: 5f296dc9aedf96c3258dc256d9bc8fc8fdf05f12
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774175"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a>Festlegen der PAGE_VERIFY-Datenbankoption auf CHECKSUM
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel überprüft, ob die PAGE_VERIFY-Datenbankoption auf CHECKSUM festgelegt ist. Wenn CHECKSUM für die PAGE_VERIFY-Datenbankoption angegeben wird, berechnet [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] beim Schreiben der Seite auf den Datenträger eine Prüfsumme des Inhalts der gesamten Seite und speichert den Wert im Seitenkopf. Wenn die Seite vom Datenträger gelesen wird, wird die Prüfsumme erneut berechnet und mit dem im Seitenkopf gespeicherten Prüfsummenwert verglichen. Dadurch wird ein hohes Maß an Integrität der Datendateien bereitgestellt.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die PAGE_VERIFY-Datenbankoption auf CHECKSUM fest.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
