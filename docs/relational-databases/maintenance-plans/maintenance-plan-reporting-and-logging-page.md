---
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
ms.openlocfilehash: db045eeb48bc04abb415bb5ac14a7872fc805b09
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754535"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a>Wartungsplan (Dialogfeld 'Berichterstellung und Protokollierung')
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Mit dem Dialogfeld **Berichterstellung und Protokollierung** können Sie die Berichte und Protokolle konfigurieren, die beim Ausführen von Wartungsplänen generiert werden.  
  
## <a name="options"></a>Tastatur  
 **Textdateibericht generieren**  
 Mit dieser Option können Sie angeben, ob [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Textdateibericht erstellen soll.  
  
 **Neue Datei erstellen**  
 Erstellt eine neue Berichtsdatei für jede Ausführung des Wartungsplans. Standardmäßig werden die Berichtsdateien auf den Computer geschrieben, der als Host der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fungiert, die diesen Wartungsplan enthält. Die Dateien werden in dem während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] festgelegten Standardprotokollordner gespeichert. Wenn Sie einen anderen Ordner angeben möchten, geben Sie im Textfeld **Ordner** den vollständigen Ordnerpfad ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen ( **...** ), und navigieren Sie zum gewünschten Ordner.  
  
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
  
  
