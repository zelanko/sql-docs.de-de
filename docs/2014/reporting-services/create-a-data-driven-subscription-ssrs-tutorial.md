---
title: Erstellen eines datengesteuerten Abonnements (SSRS-Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], tutorials
- walkthroughs [Reporting Services]
- data-driven subscriptions
ms.assetid: 79ab0572-43e9-4dc4-9b5a-cd8b627b8274
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6e1399c97e77a2b7b0bb68a8022effefb1d4814
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59964106"
---
# <a name="create-a-data-driven-subscription-ssrs-tutorial"></a>Erstellen eines datengesteuerten Abonnements (SSRS-Lernprogramm)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ermöglicht datengesteuerte Abonnements, sodass Sie die Verteilung eines Berichts auf der Basis dynamischer Abonnentendaten anpassen können. Datengesteuerte Abonnements sind für folgende Arten von Szenarios gedacht:  
  
-   Verteilen von Berichten an einen großen Empfängerpool, dessen Mitglieder sich bis zur nächsten Verteilung ändern können. Beispiel: das Verteilen eines Monatsberichts an alle aktuellen Kunden.  
  
-   Verteilen von Berichten an eine spezifische Empfängergruppe, die anhand vordefinierter Kriterien ermittelt wird. Beispiel: das Versenden eines Umsatzberichts an die zehn führenden Verkaufsmanager einer Organisation.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie datengesteuerte Abonnements verwendet werden. Hierbei wird ein einfaches Beispiel zum Veranschaulichen der Konzepte verwendet.  
  
 Dieses Lernprogramm ist in drei Lektionen aufgeteilt:  
  
 [Lektion 1: Erstellen einer Beispiel-Abonnentendatenbank](lesson-1-creating-a-sample-subscriber-database.md)  
 In dieser Lektion erfahren Sie, wie eine lokale [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank erstellt wird, die Abonnenteninformationen enthält.  
  
 [Lektion 2: Ändern der Eigenschaften der Berichtsdatenquelle](lesson-2-modifying-the-report-data-source-properties.md).  
 In dieser Lektion erfahren Sie, wie Berichtsdatenquelleneigenschaften so geändert werden können, dass der Bericht unbeaufsichtigt ausgeführt werden kann. Für die unbeaufsichtigte Verarbeitung sind gespeicherte Anmeldeinformationen erforderlich. Sie ändern auch das Berichtsdataset, um einen Parameter einzuschließen, der von den Abonnentendaten angegeben wird.  
  
 [Lektion 3: Definieren eines datengesteuerten Abonnements](lesson-3-defining-a-data-driven-subscription.md)  
 In dieser Lektion erfahren Sie, wie ein datengesteuertes Abonnement definiert wird. In dieser Lektion werden Sie durch die einzelnen Seiten im Assistenten für das datengesteuerte Abonnement geführt.  
  
## <a name="requirements"></a>Anforderungen  
 Datengesteuerte Abonnements werden normalerweise von einem Berichtsserveradministrator erstellt und verwaltet. Für das Anlegen von datengesteuerten Abonnements sind Erfahrungen im Erstellen von Abfragen, Kenntnisse darüber, welche Datenquellen Abonnentendaten enthalten, und erhöhte Berechtigungen auf einem Berichtsserver erforderlich.  
  
 Das Lernprogramm verwendet den in diesem Tutorial erstellten Bericht [Erstellen eines einfachen Tabellenberichts &#40;SSRS-Tutorial&#41; ](create-a-basic-table-report-ssrs-tutorial.md) und Daten aus [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]  
  
 Auf Ihrem System müssen zum Verwenden dieses Lernprogramms folgende Anwendungen installiert sein:  
  
-   Eine Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die datengesteuerte Abonnements unterstützt. Weitere Informationen finden Sie unter [Editionen und Komponenten von SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).  
  
-   Der Berichtsserver muss im einheitlichen Modus ausgeführt werden. Die in diesem Lernprogramm beschriebene Benutzeroberfläche basiert auf einem Berichtsserver im einheitlichen Modus. Abonnements werden auf Berichtsservern im SharePoint-Modus unterstützt, aber die Benutzeroberfläche weicht von der die in diesem Lernprogramm beschriebenen ab.  
  
-   Der SQL Server-Agent-Dienst muss ausgeführt werden.  
  
-   Ein Bericht mit Parametern. Dieses Tutorial geht von dem Beispielbericht `Sales Orders` aus, den Sie mit dem Tutorial [Erstellen eines einfachen Tabellenberichts &#40;SSRS-Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md).  
  
-   Die [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Beispieldatenbank, die Daten für den Beispielbericht bereitstellt.  
  
-   Eine Rollenzuordnung, welche die Aufgabe Alle Abonnements verwalten für den Beispielbericht umfasst. Diese Aufgabe ist für das Definieren eines datengesteuerten Abonnements erforderlich. Wenn Sie als Administrator am Computer angemeldet sind, gewährt die standardmäßige Rollenzuweisung für lokale Administratoren die zum Erstellen datengesteuerter Abonnements erforderlichen Berechtigungen. Weitere Informationen finden Sie unter [Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md).  
  
-   Ein freigegebener Ordner, für den Sie Schreibberechtigungen besitzen. Auf den freigegebenen Ordner muss über eine Netzwerkverbindung zugegriffen werden können.  
  
 **Ungefähre Dauer dieses Tutorials:** 30 Minuten. Zusätzliche 30 Minuten werden benötigt, wenn Sie das Lernprogramm für grundlegende Berichte nicht abgeschlossen haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md)   
 [Erstellen eines einfachen Tabellenberichts &#40;SSRS-Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
