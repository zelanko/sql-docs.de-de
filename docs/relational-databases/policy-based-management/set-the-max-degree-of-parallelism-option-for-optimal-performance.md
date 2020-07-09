---
title: Maximaler Grad an Parallelität und richtlinienbasierte Verwaltung
description: Beschreibt das Konfigurieren einer Richtlinie, um den maximalen Grad an Parallelität für die richtlinienbasierte Verwaltung von SQL Server zu überprüfen.
ms.custom: seo-lt-2019
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9f2cd688ca16baad21ec295105eeb0fdbbbda967
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774186"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Festlegen der 'Max. Grad an Parallelität'-Option auf optimale Leistung
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel bestimmt, ob die Max. Grad an Parallelität-Option (MAXDOP) einen Wert größer als 8 hat. Wird diese Option auf einen größeren Wert festgelegt, führt dies häufig zu unerwünschtem Ressourcenverbrauch und zu Leistungseinbußen.  
  
## <a name="best-practice-recommendations"></a>Empfehlungen zu bewährten Methoden  
 Die Konfigurationsoption „Max. Grad an Parallelität“ (MAXDOP) steuert die Anzahl der Prozessoren, die für die Ausführung einer Abfrage in einem parallelen Plan verwendet werden. Diese Option bestimmt die Anzahl an Threads, die für die Abfrageplanoperatoren verwendet werden, die die Arbeit parallel ausführen. Je nachdem, ob SQL Server auf einem symmetrischen Multiprocessingcomputer (SMP), einem Computer mit nicht einheitlichem Speicherzugriff (NUMA) oder für hyperthreadingfähige Prozessoren eingerichtet ist, können Sie die Option „Max. Grad an Parallelität“ den Anforderungen entsprechend konfigurieren. 
 
 Empfehlungen für das Konfigurieren von MAXDOP hängen von der verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version ab. Versionsspezifische Anleitungen finden Sie im Artikel [Konfigurieren der Serverkonfigurationsoption „Max. Grad an Parallelität“](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines). Konfigurieren Sie die Richtlinie, um den Wert für die Option „Max. Grad an Parallelität“ entsprechend zu überprüfen.     
  
## <a name="for-more-information"></a>Weitere Informationen finden Sie unter  
 [Empfehlung und Richtlinien für die Konfigurationsoption „Max. Grad an Parallelität“ in SQL Server](https://go.microsoft.com/fwlink/?linkid=117786)    
 [Konfigurieren der Serverkonfigurationsoption „Max. Grad an Parallelität“](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)     
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)     
  
