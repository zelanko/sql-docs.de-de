---
description: Wartungsplan (Dialogfeld 'Berichterstellung und Protokollierung')
title: Wartungsplan (Dialogfeld „Berichterstellung und Protokollierung“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 05db1c0f8c2eacd2a30e1e1e50b08e090ca6e9c4
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88420864"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a>Wartungsplan (Dialogfeld 'Berichterstellung und Protokollierung')
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Mit dem Dialogfeld **Berichterstellung und Protokollierung** können Sie die Berichte und Protokolle konfigurieren, die beim Ausführen von Wartungsplänen generiert werden.  
  
## <a name="options"></a>Tastatur  
 **Textdateibericht generieren**  
 Mit dieser Option können Sie angeben, ob [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Textdateibericht erstellen soll.  
  
 **Erstellen einer neuen Datei**  
 Erstellt eine neue Berichtsdatei für jede Ausführung des Wartungsplans. Standardmäßig werden die Berichtsdateien auf den Computer geschrieben, der als Host der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fungiert, die diesen Wartungsplan enthält. Die Dateien werden in dem während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] festgelegten Standardprotokollordner gespeichert. Wenn Sie einen anderen Ordner angeben möchten, geben Sie im Textfeld **Ordner** den vollständigen Ordnerpfad ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen (**...**), und navigieren Sie zum gewünschten Ordner.  
  
 **An Datei anfügen**  
 Fügt die jeweiligen Berichte der einzelnen Planausführungen an die Datei an, die im Textfeld **Dateiname** angegeben wurde. Sie können auch eine Datei angeben, indem Sie auf die Schaltfläche zum Durchsuchen klicken und im angezeigten Dialogfeld eine Datei auswählen.  
  
 **Bericht an einen E-Mail-Empfänger senden**  
 Übermittelt das Ergebnis einer Wartungsplanausführung per E-Mail. Diese Option ist nur verfügbar, wenn Datenbank-E-Mail aktiviert und ordnungsgemäß konfiguriert ist.  
  
 **Agentoperator**  
 Wählen Sie einen Agentoperator aus der Liste aus, der als E-Mail-Empfänger festgelegt werden soll. Diese Option ist nur verfügbar, wenn Datenbank-E-Mail aktiviert und ordnungsgemäß konfiguriert ist.  
  
 **Erweiterte Informationen protokollieren**  
 Mit dieser Option enthält das Protokoll mehr Informationen. Durch Verwenden dieser Option wird der gespeicherte Wartungsplanverlauf umfangreicher.  
  
 **Auf Remoteserver protokollieren**  
 Protokolliert den Wartungsplanverlauf auf einem Remoteserver.  
  
 **Connection**  
 Gibt die Verbindungsinformationen an, die beim Protokollieren auf einem Remoteserver verwendet werden sollen.  
  
 **Neu**  
 Zeigt das Dialogfeld **Verbindungseigenschaften** an. Dient dem Konfigurieren neuer Verbindungsinformationen zum Protokollieren auf einem Remoteserver.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)  
  
  
