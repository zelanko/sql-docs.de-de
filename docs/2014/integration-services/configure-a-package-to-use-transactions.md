---
title: Konfigurieren eines Pakets für die Verwendung von Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], configuring packages to use
ms.assetid: 8bf14957-27b4-456b-81d9-e1a0e0ca94b7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 16d1f0f4c24f18327ee31da1fb85a74d19588384
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66060863"
---
# <a name="configure-a-package-to-use-transactions"></a>Konfigurieren eines Pakets für die Verwendung von Transaktionen
  Beim Konfigurieren eines Pakets zur Verwendung von Transaktionen stehen zwei Optionen zur Verfügung:  
  
-   Eine einzelne Transaktion für das Paket. In diesem Fall wird diese Transaktion durch das Paket selbst *initiiert* , während einzelne Tasks und Container des Pakets an dieser einzelnen Transaktion beteiligt sind.  
  
-   Mehrere Transaktionen im Paket. In diesem Fall unterstützt das Paket Transaktionen, die Transaktionen werden jedoch tatsächlich von einzelnen Tasks und Containern im Paket initiiert.  
  
 Im Folgenden wird beschrieben, wie beide Optionen konfiguriert werden.  
  
## <a name="configuring-a-single-transaction"></a>Konfigurieren einer einzelnen Transaktion  
 Mit dieser Option initiiert das Paket selbst eine einzelne Transaktion. Sie konfigurieren das Paket zum Initiieren dieser Transaktion, indem Sie die transaktionoption-Eigenschaft des Pakets `Required`auf festlegen.  
  
 Danach tragen Sie bestimmte Tasks und Container in dieser einzelnen Transaktion ein. Zum Eintragen eines Tasks oder Containers in einer Transaktion legen Sie die transaktionoption-Eigenschaft dieses Tasks oder Containers auf `Supported`fest.  
  
#### <a name="to-configure-a-package-to-use-a-single-transaction"></a>So konfigurieren Sie ein Paket zur Verwendung einer einzelnen Transaktion  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, für das Sie die Verwendung einer Transaktion konfigurieren möchten.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Klicken Sie mit der rechten Maustaste an einer beliebigen Stelle im Hintergrund der Entwurfsoberfläche der Ablaufsteuerung, und klicken Sie anschließend auf **Eigenschaften**.  
  
5.  Legen Sie im Fenster **Eigenschaften** die transaktionoption-Eigenschaft auf `Required`fest.  
  
6.  Klicken Sie auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** mit der rechten Maustaste auf den Task oder den Container, für den Sie die Transaktion registrieren möchten, und klicken Sie auf **Eigenschaften**.  
  
7.  Legen Sie im Fenster **Eigenschaften** die transaktionoption-Eigenschaft auf `Supported`fest.  
  
    > [!NOTE]  
    >  Um eine Verbindung in einer Transaktion einzutragen, registrieren Sie die Tasks, die die Verbindung verwenden, für die Transaktion. Weitere Informationen finden Sie unter [Integration Services-Verbindungen &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md).  
  
8.  Wiederholen Sie die Schritte 6 und 7 für alle Tasks und Container, für die Sie die Transaktion registrieren möchten.  
  
## <a name="configuring-multiple-transactions"></a>Konfigurieren mehrerer Transaktionen  
 Mit dieser Option unterstützt das Paket selbst Transaktionen, startet jedoch keine Transaktion. Sie konfigurieren das Paket für die Unterstützung von Transaktionen, indem Sie die transaktionoption- `Supported`Eigenschaft des Pakets auf festlegen.  
  
 Danach konfigurieren Sie die gewünschten Tasks und Container im Paket, um Transaktionen zu initiieren oder an Transaktionen teilzunehmen. Zum Konfigurieren eines Tasks oder Containers zum Initiieren einer Transaktion legen Sie die transaktionoption-Eigenschaft dieses Tasks oder Containers auf `Required`fest.  
  
#### <a name="to-configure-a-package-to-use-multiple-transactions"></a>So konfigurieren Sie die Verwendung mehrerer Transaktionen für ein Paket  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, das Sie für die Verwendung von Transaktionen konfigurieren möchten.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Klicken Sie mit der rechten Maustaste an einer beliebigen Stelle im Hintergrund der Entwurfsoberfläche der Ablaufsteuerung, und klicken Sie anschließend auf **Eigenschaften**.  
  
5.  Legen Sie im Fenster **Eigenschaften** die transaktionoption-Eigenschaft auf `Supported`fest.  
  
    > [!NOTE]  
    >  Das Paket unterstützt Transaktionen, aber die Transaktionen werden von Tasks oder Containern im Paket gestartet.  
  
6.  Klicken Sie auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** mit der rechten Maustaste auf den Task oder den Container im Paket, für den Sie eine Transaktion starten möchten, und klicken Sie auf **Eigenschaften**.  
  
7.  Legen Sie im Fenster **Eigenschaften** die transaktionoption-Eigenschaft auf `Required`fest.  
  
8.  Wenn eine Transaktion von einem Container gestartet wird, klicken Sie mit der rechten Maustaste auf den Task oder den Container, für den Sie die Transaktion registrieren möchten, und klicken Sie auf **Eigenschaften**.  
  
9. Legen Sie im Fenster **Eigenschaften** die transaktionoption-Eigenschaft auf `Supported`fest.  
  
    > [!NOTE]  
    >  Um eine Verbindung in einer Transaktion einzutragen, registrieren Sie die Tasks, die die Verbindung verwenden, für die Transaktion. Weitere Informationen finden Sie unter [Integration Services-Verbindungen &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md).  
  
10. Wiederholen Sie die Schritte 6 bis 9 für alle Tasks und Container, die eine Transaktion initiieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Transaktionen](integration-services-transactions.md)  
  
  
