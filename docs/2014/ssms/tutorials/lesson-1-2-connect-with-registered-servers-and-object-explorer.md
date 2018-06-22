---
title: Herstellen einer Verbindung mit registrierten Servern und dem Objekt-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
caps.latest.revision: 49
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7d022b889673ddc918859ebf474440438a9e564a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058621"
---
# <a name="connect-with-registered-servers-and-object-explorer"></a>Herstellen einer Verbindung mit registrierten Servern und dem Objekt-Explorer
  Dieses Lernprogramm veranschaulicht die Verwendung von registrierten Servern und Objekt-Explorer.  
  
 Dieses Lernprogramm verwendet die Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert. Weitere Informationen finden Sie unter [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).  
  
## <a name="connecting-to-servers"></a>Herstellen einer Verbindung mit Servern  
 Auf der Symbolleiste der Komponente Registrierte Server befinden sich Schaltflächen für [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Zur Vereinfachung der Verwaltung können Sie einen oder mehrere dieser Servertypen registrieren. In der folgenden Übung werden Sie die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank registrieren.  
  
#### <a name="to-register-the-database"></a>So registrieren Sie die Datenbank  
  
1.  Klicken Sie auf der Symbolleiste Registrierte Server auf **Datenbank-Engine**, falls erforderlich. (Dieser Knoten ist möglicherweise bereits ausgewählt.)  
  
2.  Erweitern Sie **Datenbank-Engine**.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Lokale Servergruppen**und anschließend auf **Neue Serverregistrierung**.  
  
4.  Geben Sie im Dialogfeld **Neue Serverregistrierung** im Textfeld **Servername** den Namen Ihrer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]an.  
  
5.  Geben Sie im Feld **Name des registrierten Servers** den Namen [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]ein.  
  
6.  Wählen Sie auf der Registerkarte **Verbindungseigenschaften** in der Liste **Verbindung mit Datenbank herstellen** den Eintrag **\<Server durchsuchen…>** aus.  
  
7.  Klicken Sie im Dialogfeld **Nach Datenbanken suchen** auf **Ja**.  
  
8.  Wählen Sie im Dialogfeld **Server nach Datenbank durchsuchen** den Eintrag [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]aus, und klicken Sie dann auf **OK**.  
  
9. Um sicherzustellen, dass der Server ordnungsgemäß registriert wurde, klicken Sie auf **Testen**.  
  
10. Klicken Sie im Dialogfeld **Neue Serverregistrierung** auf **Speichern**.  
  
## <a name="connecting-with-object-explorer"></a>Herstellen einer Verbindung mit dem Objekt-Explorer  
 Wie die Komponente Registrierte Server kann der Objekt-Explorer eine Verbindung mit [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]herstellen.  
  
#### <a name="to-connect-with-object-explorer"></a>So stellen Sie eine Verbindung mit dem Objekt-Explorer her  
  
1.  Klicken Sie auf der Symbolleiste vom Objekt-Explorer auf **Verbinden**, um eine Liste der möglichen Verbindungstypen anzuzeigen. Wählen Sie dann **Datenbank-Engine**aus.  
  
2.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** im Textfeld **Servername** den Namen Ihrer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]an.  
  
3.  Klicken Sie auf **Optionen** , und sehen Sie sich die Auswahlmöglichkeiten an.  
  
4.  Klicken Sie auf **Verbinden**, um eine Verbindung mit dem Server herzustellen. Wenn bereits eine Verbindung besteht, werden Sie mit dieser Aktion an den Objekt-Explorer zurückgeleitet, und der Fokus wird auf diesen Server festgelegt.  
  
     Mit dem Objekt-Explorer können Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit, den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent, die Replikation und Datenbank-E-Mail verwalten. Über den Objekt-Explorer können nur einige der Funktionen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]und [!INCLUDE[ssIS](../../includes/ssis-md.md)]verwaltet werden. Für jede dieser Komponenten gibt es zusätzliche, spezialisierte Tools.  
  
5.  Erweitern Sie im Objekt-Explorer den Ordner **Datenbanken** , und wählen Sie [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]aus.  
  
     Beachten Sie, dass [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] die Systemdatenbanken in einem separaten Ordner präsentiert.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Ändern des Umgebungslayouts](lesson-1-3-change-the-environment-layout.md)  
  
  