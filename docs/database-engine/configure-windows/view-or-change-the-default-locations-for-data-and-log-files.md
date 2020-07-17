---
title: Anzeigen oder Ändern der Standardspeicherorte für Daten- und Protokolldateien (SQL Server Management Studio) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Standardspeicherorte für SQL Server-Datendateien und -Protokolldateien anzeigen oder ändern. Sie erfahren zudem, wie Sie die Dateien mit Zugriffssteuerungslisten schützen.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9a0c720684f0eefa301e9a5387ffda54e349f85d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85680782"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>Anzeigen oder Ändern der Standardspeicherorte für Datenbankdateien
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
 Als bewährte Methode zum Schutz der Datendateien und Protokolldateien sollten Sie sicherstellen, dass diese durch Zugriffssteuerungslisten (ACLs) geschützt sind. Einrichten der ACLs für den Verzeichnisstamm, unter dem die Dateien erstellt werden.  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>Anzeigen oder Ändern der Standardspeicherorte für Datenbankdateien  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf Ihren Server, und klicken Sie auf **Eigenschaften**.  
  
2.  Klicken Sie im linken Bedienfeld auf der betreffenden Eigenschaftenseite auf die Registerkarte **Datenbankeinstellungen** .  
  
3.  Im Bereich **Standardspeicherorte für Datenbank**können Sie die aktuellen Standardspeicherorte für neue Datendateien und neue Protokolldateien anzeigen. Um einen Standardspeicherort zu ändern, geben Sie einen neuen Standardpfadnamen in das Feld **Daten** oder **Protokoll** ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen, um einen Pfadnamen zu suchen und auszuwählen.  
  
>**HINWEIS:** Nach dem Ändern der Standardspeicherorte müssen Sie den SQL Server-Dienst beenden und wieder starten, um die Änderung abzuschließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Erstellen einer Datenbank](../../relational-databases/databases/create-a-database.md)  
  
  
