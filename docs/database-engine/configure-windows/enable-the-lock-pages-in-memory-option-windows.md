---
title: Aktivieren der Option „Sperren von Seiten im Speicher“ (Windows) | Microsoft-Dokumentation
description: Informationen zum Aktivieren der Option „Seiten im Arbeitsspeicher sperren“ Hier erfahren Sie, wie Sie die Leistung steigern können, indem Sie Daten im physischen Speicher belassen, anstatt sie auf den Datenträger auszulagern.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6390c4a4bb4d8ea2ed9b5e5be1712eb7e782a29b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772474"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a>Aktivieren der Option Sperren von Seiten im Speicher (Windows)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Mit dieser Windows-Richtlinie werden die Konten bestimmt, die einen Prozess zum Speichern von Daten im physischen Speicher verwenden können, um das systemgesteuerte Auslagern der Daten in den virtuellen Arbeitsspeicher zu vermeiden.  
  
> [!NOTE]  
>  Durch Sperren von Seiten im Arbeitsspeicher kann die Leistung bei der Auslagerung von Arbeitsspeicherdaten auf die Festplatte gesteigert werden.  
  
 Verwenden Sie das Windows-Tool für Gruppenrichtlinien (gpedit.msc), um diese Richtlinie für das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendete Konto zu aktivieren. Diese Richtlinie können Sie nur ändern, wenn Sie als Systemadministrator angemeldet sind.  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a>So aktivieren Sie die Option "Sperren von Seiten im Speicher"  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**. Geben Sie **gpedit.msc** im Feld **Öffnen**ein.  
  
2.  Erweitern Sie in der Konsole **Editor für lokale Gruppenrichtlinien** die Option **Computerkonfiguration**und dann **Windows-Einstellungen**.  
  
3.  Erweitern Sie **Sicherheitseinstellungen**und dann **Lokale Richtlinien**.  
  
4.  Wählen Sie den Ordner **Zuweisen von Benutzerrechten** aus.  
  
     Die Richtlinien werden im Detailbereich angezeigt.  
  
5.  Doppelklicken Sie im Detailbereich auf **Sperren von Seiten im Speicher**.  
  
6.  Klicken Sie im Dialogfeld **Lokale Sicherheitseinstellung > Sperren von Seiten im Speicher** auf **Benutzer oder Gruppe hinzufügen**.  
  
7.  Wählen Sie im Dialogfeld **Select Users, Service Accounts, or Groups** (Benutzer, Dienstkonten oder Gruppen auswählen) das SQL Server-Dienstkonto aus.  
  
8.  Starten Sie SQL Server neu, damit diese Einstellung übernommen wird.
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen für den Serverarbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
