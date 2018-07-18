---
title: Verwenden Sie eine BI-Semantikmodellverbindung in Excel oder Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 486195ca-530f-49e8-b40d-0f817db159ee
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b1ff3dfedd5dce6a4db551cc6fdb180e4d723d8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219970"
---
# <a name="use-a-bi-semantic-model-connection-in-excel-or-reporting-services"></a>Verwenden einer BI-Semantikmodellverbindung in Excel oder Reporting Services
  In diesem Thema wird erläutert, wie die BI-Semantikmodellverbindungen verwendet werden, die gemäß den Anweisungen in anderen Themen erstellt wurden. Wenn Sie noch nicht mit einem BI-Semantikmodell erstellt haben, finden Sie unter [erstellen Sie eine BI-Semantikmodellverbindung mit einer PowerPivot-Arbeitsmappe](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md) und [Erstellen einer BI-Semantikmodellverbindung mit einer tabellarischen Modelldatenbank](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).  
  
##  <a name="bkmk_connect"></a> Herstellen einer Verbindung von Excel aus  
 Sie können eine BI-Semantikmodellverbindung als Datenquelle in Excel oder einer beliebigen anderen Geschäftsanwendung angeben, die Analysis Services-Daten im tabellarischen Modell verwendet. Dieser Abschnitt erläutert die zwei Ansätze zum Herstellen einer Verbindung mit BI-Semantikmodelldaten über Excel.  
  
 Bei BI-Semantikmodellverbindungen von Excel ist es erforderlich, dass Sie über Excel 2010 und den auf der Arbeitsstation installierten MSOLAP.5-OLE DB-Anbieter verfügen. Weitere Informationen zu Verbindungsanforderungen erhalten Sie im weiteren Verlauf dieses Abschnitts.  
  
 **Starten mit SharePoint**  
  
-   Klicken Sie mit der rechten Maustaste auf eine BI-Semantikmodellverbindung in einer Bibliothek, und wählen Sie **Excel starten**aus.  
  
 ![Screenshot des BISM-schnellstartbefehls](../media/ssas-bism-quicklaunch.gif "Screenshot des BISM-schnellstartbefehls")  
  
 Klicken Sie auf **Aktivieren** , wenn Sie zur Aktivierung der Datenverbindungen aufgefordert werden. In Excel wird eine Arbeitsmappe geöffnet, die eine mit Feldern aus der zugrunde liegenden Datenquelle gefüllte PivotTable-Feldliste enthält.  
  
 **Starten von Excel aus**  
  
1.  Starten Sie Excel, und öffnen Sie eine Arbeitsmappe. Klicken Sie auf der Registerkarte Daten unter Externe Daten abrufen auf **Aus anderen Quellen**.  
  
2.  Klicken Sie auf **Aus Analysis Services** , und importieren Sie die Daten mithilfe des Datenverbindungs-Assistenten.  
  
3.  Geben Sie die SharePoint-URL der BI-Semantikmodell-Verbindungsdatei (z. B.  **http://mysharepoint/shared Documents/mydata.bism**). Nehmen Sie bei der Option der Anmeldeinformationen das Standardprotokoll **Windows-Authentifizierung verwenden**an. Klicken Sie auf **Weiter**.  
  
4.  Klicken Sie auf der nächsten Seite erneut auf **Weiter** . Obwohl Sie aufgefordert werden, eine Datenbank auszuwählen, können Sie nur die eine Datenbank verwenden, die in der BI-Semantikmodellverbindung angegeben wird.  
  
5.  Auf der letzten Seite können Sie einen Anzeigenamen und eine Beschreibung angeben. Klicken Sie auf **Fertig stellen**, und klicken Sie dann im Dialogfeld zum Importieren von Daten auf **OK** , um die Daten zu importieren.  
  
 Damit Verbindungen erfolgreich sind, müssen Excel 2010 und MSOLAP.5.dll auf dem Clientcomputer installiert sein. Sie können den Anbieter erhalten, durch die Installation von der Version von PowerPivot für Excel, die für diese Version aktuell ist oder Sie können nur die Analysis Services OLE DB-Anbieter aus der [Feature Pack-Downloadseite](http://go.microsoft.com/fwlink/?linkid=214066).  
  
 Um zu bestätigen, dass MSOLAP.5.dll die aktuelle Version ist, überprüfen Sie `HKEY_CLASSES_ROOT\MSOLAP` in der Registrierung. `CurVer` muss auf Msolap. 5 festgelegt werden.  
  
 Sie müssen auch über Leseberechtigungen für die BI-Semantikmodelldatei in SharePoint verfügen. Leseberechtigungen schließen Downloadrechte ein. Excel lädt die BI-Semantikmodell-Verbindungsinformationen von SharePoint herunter und öffnet über `HTTP Get` eine direkte Verbindung mit der Datenbank. Verbindungsanforderungen werden erst dann für SharePoint übernommen, wenn die BI-Semantikmodell-Verbindungsinformationen lokal gespeichert werden.  
  
 Wenn Sie eine Verbindung mit einer tabellarischen Modelldatenbank herstellen, die auf einem Analysis Services-Server ausgeführt wird, sind SharePoint-Berechtigungen nicht ausreichend. Sie müssen auch über Leseberechtigungen für die Datenbank auf dem Server verfügen. Dieser Schritt sollte ausgeführt werden, wenn Sie die BI-Semantikmodellverbindung herstellen. Weitere Informationen finden Sie unter [Erstellen einer BI-Semantikmodellverbindung mit einer tabellarischen Modelldatenbank](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).  
  
##  <a name="bkmk_use"></a> Herstellen einer Verbindung von Reporting Services in SharePoint aus  
 Sie können eine BI-Semantikmodellverbindung auf die gleiche Weise wie die meisten Datenquellen verwenden, indem Sie die Datei als Datenquelle im Dokument oder Tool angeben, das die Daten nutzt. Obwohl eine BI-Semantikmodellverbindung auf eine physische Datenbank auf einem anderen Server verweist, verwenden Sie die Verbindungsdatei, als sei sie die Datenquelle. Die SharePoint-URL der BI-Semantikmodellverbindung stellt einen gültigen Datenquellspeicherort für [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Berichte dar, die BI-Semantikmodelldaten verwenden.  
  
 Für einen Ad-hoc-Berichtsentwurf in SharePoint muss der Benutzer, der den Bericht erstellt, über SharePoint-Berechtigungen für die BI-Semantikmodell-Verbindungsdatei (BISM-Datei) und für die Business Intelligence-Semantikmodelldatenbank verfügen. Der Sicherheitskontext der Verbindung ist der interaktive Benutzer, der den Bericht erstellt.  
  
  
