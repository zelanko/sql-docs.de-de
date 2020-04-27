---
title: Bereitstellen von Feedback für SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- sending feedback to Microsoft
- errors [SQL Server], feedback reporting
- feedback [SQL Server]
- submitting feedback [SQL Server]
- bug reporting [SQL Server]
- reporting usage information to Microsoft
- reporting errors to Microsoft
- SQL Server, feedback reporting
- documentation feedback [SQL Server]
- usage information reporting [SQL Server]
- product feedback [SQL Server]
- automatic error or usage reporting
ms.assetid: 28f3ebf0-ad71-4816-86a6-18a46f023cfe
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10466721f50dd8b090b5d6b1a06b5bffd6e5289d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62772277"
---
# <a name="providing-feedback-for-sql-server-2014"></a>Senden von Feedback zu SQL Server 2014
  [!INCLUDE[msCoName](../includes/msconame-md.md)] möchte Ihnen dafür danken, dass Sie sich die Zeit nehmen, uns beim Verbessern unserer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Produkte und der zugehörigen Dokumentation zu helfen. Sie können Vorschläge zu den Produktfunktionen und zur Benutzeroberfläche sowie Fehlerberichte weitergeben, Feedback zur Dokumentation geben und sich dazu entschließen, Fehlerberichte und Verwendungsdaten automatisch an [!INCLUDE[msCoName](../includes/msconame-md.md)] zu senden. Jede dieser drei Feedbackoptionen wird hier beschrieben.  
  
## <a name="submitting-feedback-about-the-product"></a>Senden von Feedback zum Produkt  
 Nutzen Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Feedbackseite auf [!INCLUDE[msCoName](../includes/msconame-md.md)] Connect, um Fehlerberichte und Vorschläge zu den Funktionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu senden. Diese Funktionen schließen auch Tools und Hilfsprogramme, Sprachversionen und Programmierschnittstellen ein.  
  
 Sie können auf viele verschiedene Arten auf die [!INCLUDE[msCoName](../includes/msconame-md.md)] Connect [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Feedbackseite zugreifen.  
  
-   Gehen Sie auf die [!INCLUDE[msCoName](../includes/msconame-md.md)] Connect [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Feedback-[Webseite](https://go.microsoft.com/fwlink/?linkid=34178).  
  
-   Klicken Sie in der Hilfesymbolleiste von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] auf die Schaltfläche **Feedback senden**, oder wählen Sie den Befehl **Community/Feedback senden** aus.  
  
-   Klicken Sie in der Hilfesymbolleiste von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] auf die Schaltfläche **Feedback senden**.  
  
-   Klicken Sie in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation oben in einem Thema auf die Schaltfläche **Feedback senden**.  
  
 Die Hilfesymbolleiste wird in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] oder [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] erst angezeigt, wenn Sie eine der folgenden Aktionen ausgeführt haben:  
  
-   Greifen Sie vom Hilfsprogramm aus auf die Hilfe zu.  
  
-   Aktivieren Sie das Kontrollkästchen **Hilfe** auf der Registerkarte **Symbolleisten** des Befehls Extras **/anpassen...** .  
  
## <a name="automatic-error-and-usage-reporting"></a>Automatische Fehler- und Verwendungsberichte  
 Sie können festlegen, dass automatisch Fehlerberichte und Daten über Ihre Nutzung der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Software und -Dienste an Microsoft gesendet werden. [!INCLUDE[msCoName](../includes/msconame-md.md)] verwendet diese Informationen, um die Funktionalität von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu verbessern. Alle Daten werden vertraulich behandelt.  
  
### <a name="managing-automatic-usage-reporting"></a>Verwalten der automatischen Fehlerberichterstellung  
 Dank der automatischen Verwendungsberichterstattung können Sie entscheiden, ob Sie Daten sammeln und an [!INCLUDE[msCoName](../includes/msconame-md.md)] senden möchten. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet zwei Pipelines zum Übertragen der Verwendungsdaten. Diese beiden Pipelines übertragen ähnliche Daten, aber für verschiedene Programme, und sie können unabhängig voneinander aktiviert oder deaktiviert werden. Durch das Aktivieren oder Deaktivieren einer Pipeline durch eines der Programme, wird gleichzeitig die Datensammlung für andere Programme, die ebenfalls diese Pipeline verwenden, aktiviert bzw. deaktiviert.  
  
-   Eine Pipeline wird zur Übertragung von Verwendungsdaten für alle Komponenten von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet. Eine Ausnahme bilden lediglich die Daten zur Onlinedokumentation und die Daten zu einigen Elementen der [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio-basierten Benutzerschnittstelle in den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Tools. Nach dem Setup können Sie diese Pipeline wieder deaktivieren bzw. aktivieren. Öffnen Sie dazu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-basiertes Projekt. Wählen Sie anschließend im Menü **Hilfe** die Option **Kunden-Feedbackoptionen** aus. Dieser Befehl wird nach dem Öffnen eines [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-basierten Projekts angezeigt.  
  
-   Die andere Pipeline wird für die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation, die auf Visual Studio basierenden Benutzeroberflächenelemente der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Tools und Visual Studio verwendet. Nach dem Setup können Sie diese Pipeline wieder deaktivieren bzw. aktivieren. Öffnen Sie dazu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-basiertes Projekt. Wählen Sie anschließend im Menü **Hilfe** die Option **Kunden-Feedbackoptionen** aus. Dieser Befehl wird nach dem Öffnen eines [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-basierten Projekts angezeigt.  
  
## <a name="helping-build-a-better-books-online"></a>Ihr Beitrag zu einer noch besseren Onlinedokumentation  
 Indem Sie sich für eine Aktivierung der Erstellung von Verwendungsberichten zur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation entscheiden, können Sie das Team dabei unterstützen, eine noch bessere Dokumentation zu entwickeln. Die aggregierten Daten, die wir erhalten, helfen uns dabei, die Bedürfnisse unserer Kunden besser zu verstehen. Wir können sehen, wie sie sich zwischen den Themen umherbewegen, wie oft sie sich bestimmte Themen ansehen und welche Themen sie als am nützlichsten/am wenigsten nützlich einschätzen.  
  
 Dank Ihres Feedbacks können wir verstehen, wie Sie unsere Dokumentation nutzen. Dadurch können wir unsere Dokumentationsteams dafür einsetzen, an den wichtigsten Themen zu arbeiten, und wir können künftige Dokumentationssysteme für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] entwickeln. Außerdem helfen uns die Informationen über die Verwendung der Onlinedokumentation dabei, die Funktionen zu identifizieren, für die die Kunden häufig Hilfe benötigen. Dies deutet auf Bereiche hin, deren Benutzerfreundlichkeit möglicherweise verbessert werden muss.  
  
  
