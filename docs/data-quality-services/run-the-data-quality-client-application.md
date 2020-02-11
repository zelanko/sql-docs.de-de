---
title: Ausführen der Data Quality-Clientanwendung
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.browseforservers.f1
- sql13.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: swinarko
ms.author: sawinark
ms.openlocfilehash: da099b6a3aca31dd0acdc82f7e2bdbdf13c7c24e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75244131"
---
# <a name="run-the-data-quality-client-application"></a>Ausführen der Data Quality-Clientanwendung

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Führen Sie [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]aus, und melden Sie sich bei einem [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]an.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Voraussetzungen  
 Sie müssen die Installation des [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] durch Ausführen der Datei DQSInstaller.exe abgeschlossen haben. Weitere Informationen finden Sie unter [Ausführen von DQSInstaller.exe zum Abschließen der Installation von Data Quality Server](../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Um sich bei [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]anzumelden, muss der Benutzer einer der drei Rollen (dqs_administrator, dqs_kb_editor oder dqs_kb_operator) in der DQS_MAIN-Datenbank angehören.  
  
##  <a name="Run"></a>Ausführen Data Quality-Client  
 So führen Sie [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] auf dem Computer aus, auf dem Sie ihn installiert haben:  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, klicken Sie auf **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]** und anschließend auf **Data Quality Services**, und klicken Sie dann auf **Data Quality Client**.  
  
2.  Gehen Sie im Dialogfeld **Verbindung mit Server herstellen** wie folgt vor:  
  
    1.  Geben Sie den Server an, mit dem Sie die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Anwendung verbinden möchten. Wählen Sie **(LOCAL)** aus, um eine Verbindung mit [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] auf dem lokalen Computer herzustellen. Sie können auch auf den Pfeil nach unten und dann auf ** \<Netzwerk durchsuchen klicken, um weitere Server>** , um eine Verbindung mit einem anderen Server herzustellen (oder um eine Verbindung mit dem lokalen Server nach Name herzustellen). Das Dialogfeld **Nach Servern suchen** wird angezeigt. Sie können auf der Registerkarte **Lokale Server** oder auf der Registerkarte **Netzwerkserver** einen Server auswählen.  
  
    2.  Zum Verschlüsseln der Datenübertragung zwischen [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] und [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]klicken Sie auf **Optionen**und aktivieren dann das Kontrollkästchen **Verbindung verschlüsseln** .  
  
3.  Klicken Sie auf **Verbinden**.  
  
 Der [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm wird angezeigt. Weitere Informationen hierzu finden Sie unter [Startbildschirm des Data Quality-Clients](../data-quality-services/data-quality-client-home-screen.md).  
  
  
