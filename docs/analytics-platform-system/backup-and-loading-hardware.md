---
title: Sicherung und Laden von Hardware – Parallel Data Warehouse
description: Um Ihre End-to-End Data warehousing-Lösung für Analytics Platform System (APS) mit Parallel Data Warehouse (PDW) bereitzustellen, müssen Sie einen Plan aus, um das Datawarehouse zu sichern, und Laden von Daten erstellen. Verwenden Sie diese Anleitung zum Abrufen und Konfigurieren von Sicherung und Laden von Servern, die Ihren geschäftlichen Anforderungen erfüllt.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 90f142a8bb86f99ed5cf5d9ff926bdf849060324
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961418"
---
# <a name="backup-and-loading-hardware-overview---parallel-data-warehouse"></a>Sicherung und Laden von Hardwareübersicht: Parallel Data Warehouse
Um Ihre End-to-End Data warehousing-Lösung für Analytics Platform System (APS) mit Parallel Data Warehouse (PDW) bereitzustellen, müssen Sie einen Plan aus, um das Datawarehouse zu sichern, und Laden von Daten erstellen. Verwenden Sie diese Anleitung zum Abrufen und Konfigurieren von Sicherung und Laden von Servern, die Ihren geschäftlichen Anforderungen erfüllt.  
  
## <a name="acquire-and-configure-backup-servers"></a>Erwerben Sie und konfigurieren Sie die backup-Server  
![Sichern von Prozess](media/backup-process.png "Prozess sichern")  
  
Um einen PDW-Datenbank zu sichern, benötigen Sie mindestens eine backup-Server. Sie können Ihre eigenen vorhandenen Hardware oder Erwerb neuer Hardware. Weitere Informationen finden Sie unter [abrufen und Konfigurieren eines Servers für die Sicherung](acquire-and-configure-backup-server.md). Diese Anweisungen beinhalten eine [Backup Server Worksheet zur kapazitätsplanung eines](backup-capacity-planning-worksheet.md) können Sie die richtige Lösung für die Sicherung planen.  
  
## <a name="acquire-and-configure-loading-servers"></a>Erwerben Sie und konfigurieren Sie beim Laden von Servern  
![Prozess des Ladens](media/loading-process.png "Prozess des Ladens")  
  
Um Daten zu laden, benötigen Sie eine oder mehrere beim Laden von Servern. Können Sie Ihre eigenen vorhandenen ETL- oder anderen Servern, oder Sie können neue Server erwerben. Weitere Informationen finden Sie unter [abrufen und Konfigurieren eines ladenden Servers](acquire-and-configure-loading-server.md). Diese Anweisungen beinhalten eine [laden Server Worksheet zur kapazitätsplanung eines](loading-server-capacity-planning-worksheet.md) helfen Ihnen beim Planen der richtigen Lösung für das Laden.  
  
## <a name="see-also"></a>Siehe auch  
[Sichern und Wiederherstellen – Übersicht](backup-and-restore-overview.md)  
[– Übersicht](load-overview.md)  
  
