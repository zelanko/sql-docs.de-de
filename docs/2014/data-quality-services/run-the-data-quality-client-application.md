---
title: Ausführen der Data Quality-Clientanwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 18054a5e6a2393a2a16baf81caa44a72489e7fc5
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937421"
---
# <a name="run-the-data-quality-client-application"></a>Ausführen der Data Quality-Clientanwendung
  Sie können [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) verwenden, indem Sie [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ausführen und sich bei einem [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] anmelden.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Sie müssen die Installation des [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] durch Ausführen der Datei DQSInstaller.exe abgeschlossen haben. Weitere Informationen finden Sie unter [Ausführen von DQSInstaller.exe zum Abschließen der Installation von Data Quality Server](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Um sich bei [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]anzumelden, muss der Benutzer einer der drei Rollen (dqs_administrator, dqs_kb_editor oder dqs_kb_operator) in der DQS_MAIN-Datenbank angehören.  
  
##  <a name="run-data-quality-client"></a><a name="Run"></a>Ausführen Data Quality-Client  
 Um [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] auf dem Computer auszuführen, auf dem Sie ihn installiert haben, fahren Sie wie folgt fort:  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, klicken Sie auf **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]** und anschließend auf **Data Quality Services**, und klicken Sie dann auf **Data Quality Client**.  
  
2.  Gehen Sie im Dialogfeld **Verbindung mit Server herstellen** wie folgt vor:  
  
    1.  Geben Sie den Server an, mit dem Sie die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Anwendung verbinden möchten. Wählen Sie **(LOCAL)** aus, um eine Verbindung mit [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] auf dem lokalen Computer herzustellen. Sie können auch auf den Pfeil nach unten klicken und auswählen **\<Browse network for more servers>** , um eine Verbindung mit einem anderen Server herzustellen (oder um eine Verbindung mit dem lokalen Server nach Name herzustellen). Das Dialogfeld **Nach Servern suchen** wird angezeigt. Sie können auf der Registerkarte **Lokale Server** oder auf der Registerkarte **Netzwerkserver** einen Server auswählen.  
  
    2.  Wenn Sie die Datenübertragung zwischen [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] und [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] verschlüsseln möchten, klicken Sie auf **Optionen**, und aktivieren Sie dann das Kontrollkästchen **Verbindung verschlüsseln**.  
  
3.  Klicken Sie auf **Verbinden**.  
  
 Der [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm wird angezeigt. Weitere Informationen hierzu finden Sie unter [Startbildschirm des Data Quality-Clients](../../2014/data-quality-services/data-quality-client-home-screen.md).  
  
  
