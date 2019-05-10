---
title: Enterprise Information Management mit SSIS, MDS und DQS [Lernprogramm] | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba09b504-3007-4cb7-8ef8-f01adbf51646
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 8a9b7c9f241bdf63679db85d7408e696c6f55599
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65489728"
---
# <a name="enterprise-information-management-using-ssis-mds-and-dqs-together-tutorial"></a>Enterprise Information Management mit SSIS, MDS und DQS [Lernprogramm]
  Das Verwalten von Informationen in einem Unternehmen schließt in der Regel die Integration von Daten im gesamten Unternehmen und darüber hinaus ein, außerdem Bereinigen der Daten, Abgleichen der Daten zum Entfernen aller Duplikate, Standardisieren der Daten, Erweitern der Daten, Sicherstellen, dass die Daten gesetzliche und Kompatibilitätsanforderungen erfüllen, und Speichern der Daten an einem zentralen Ort mit allen erforderlichen Sicherheitseinstellungen.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] stellt alle für eine effektive Enterprise Information Management (EIM)-Lösung benötigten Komponenten in einem einzigen Produkt bereit. Folgende Schlüsselkomponenten bieten Unterstützung bei der Erstellung einer EIM-Lösung:  
  
-   SQL Server Integration Services  
  
-   SQL Server Data Quality Services  
  
-   SQL Server Master Data Services  
  
 SQL Server Integration Services (SSIS) stellt eine leistungsstarke, erweiterbare Plattform für das Integrieren von Daten aus verschiedenen Quellen in einer umfassenden Lösung zum Extrahieren, Transformieren und Laden von Daten (ETL-Lösung) bereit, die Geschäftsworkflows, ein Data Warehouse oder die Masterdatenverwaltung unterstützt. Finden Sie unter [Integration Services – Übersicht](https://msdn.microsoft.com/library/ms141263\(SQL.105\).aspx) Thema eine kurze Übersicht und typische Verwendungen von SSIS.  
  
 SQL Server Data Quality Services (DQS) ermöglicht es Ihnen, Daten zu bereinigen, abzugleichen, zu standardisieren und zu erweitern, sodass Sie zuverlässige Informationen für Business Intelligence, ein Data Warehouse und Transaktionsverarbeitungs-Arbeitsauslastungen übermitteln können. Finden Sie unter [Einführung in Data Quality Services](https://msdn.microsoft.com/library/ff877917.aspx) Thema geschäftsanforderung nach DQS und wie der DQS die Anforderung erfüllt.  
  
 SQL Server Master Data Services (MDS) bietet einen zentralen Datenhub, der sicherstellt, dass die Integrität der Informationen und die Einheitlichkeit der Daten in verschiedenen Anwendungen konstant sind. Finden Sie unter [Übersicht über Master Data Services](../master-data-services/master-data-services-overview-mds.md) Thema kurze Beschreibungen wichtiger Funktionen von MDS.  
  
 Finden Sie unter [Bereinigung und Abgleich von Master Data by using EIM](https://msdn.microsoft.com/library/hh403491.aspx) Whitepapers umfassende Hinweise zur Implementierung einer EIM-Lösung, die gemeinsame Verwendung dieser Microsoft EIM-Technologien und sehen Sie sich [Enterprise Informationsmanagement (EIM): Zusammenführen von SSIS, DQS und MDS](https://go.microsoft.com/fwlink/?LinkId=258672) video, um eine interessante Demo eines EIM-Szenarios.  
  
 In diesem Lernprogramm erfahren Sie, wie Sie SSIS, MDS und DQS zusammen verwenden, um eine Enterprise Information Management (EIM)-Beispiellösung zu implementieren. Zunächst erstellen Sie mithilfe von DQS eine Wissensdatenbank, die Informationen zu den Daten (Metadaten) enthält. Dann bereinigen Sie die Daten in einer Excel-Datei anhand der Wissensdatenbank und gleichen die Daten ab, um Duplikate in den Daten zu identifizieren und zu entfernen. Als Nächstes verwenden Sie das MDS-Add-In für Excel, um die bereinigten und abgeglichenen Daten in MDS hochzuladen. Dann automatisieren Sie den gesamten Prozess, indem Sie eine SSIS-Lösung verwenden. Die SSIS-Lösung in diesem Lernprogramm liest die Eingabedaten aus einer Excel-Datei, aber Sie können sie erweitern, damit sie aus verschiedenen Quellen wie Oracle, Teradata, DB2 und Windows Azure SQL-Datenbank lesen kann.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
1.  Microsoft SQL Server 2012 mit den folgenden installierten Komponenten:  
  
    1.  Integration Services (SSIS)  
  
    2.  Master Data Services (MDS)  
  
    3.  Data Quality Services (DQS)  
  
    4.  SQL Server Data Tools  
  
         Finden Sie unter [SQL Server 2012-Installationshandbuch](../database-engine/install-windows/installation-for-sql-server.md) ausführliche Informationen zum Installieren des Produkts.  
  
2.  [Konfigurieren Sie MDS mithilfe des Konfigurations-Manager für Master Data Services](https://msdn.microsoft.com/library/ee633884.aspx)  
  
     Verwenden Sie den Konfigurations-Manager, um eine Master Data Services-Datenbank zu erstellen und zu konfigurieren. Nachdem Sie die MDS-Datenbank erstellt haben, erstellen Sie eine Webanwendung für MDS auf einer Website (z. B.: [ http://localhost/MDS ](http://localhost/MDS)), und ordnen Sie die MDS-Datenbank mit der MDS-Webanwendung. Beachten Sie, dass zum Erstellen einer MDS-Webanwendung IIS auf Ihrem Computer installiert sein muss. Finden Sie unter [Anforderungen für die Webanwendung (Master Data Services)](https://msdn.microsoft.com/library/ee633744.aspx) und [Datenbankanforderungen (Master Data Services)](https://msdn.microsoft.com/library/ee633767.aspx) Weitere Informationen zu den Voraussetzungen für die MDS-Datenbank und Web-Anwendung konfigurieren.  
  
3.  [Installieren und konfigurieren Sie DQS mithilfe von Data Quality Server-Installationsprogramm](https://msdn.microsoft.com/library/hh231682.aspx). Klicken Sie auf **starten**, klicken Sie auf **Programme**, klicken Sie auf **Microsoft SQL Server 2014**, klicken Sie auf **Data Quality Services**, und klicken Sie dann auf **Data Quality Server-Installationsprogramm**.  
  
4.  Microsoft Excel 2010 (32-Bit wird bevorzugt).  
  
5.  Installieren Sie **Master Data Services-Add-in für Excel** (32-Bit oder 64-Bit-basierend auf der Version von Excel auf Ihrem Computer haben) aus [hier](https://www.microsoft.com/download/details.aspx?id=29064). Führen Sie zum Ermitteln der Version von Excel auf Ihrem Computer installierten **Excel**, klicken Sie auf **Datei** auf der Menüleiste, und klicken Sie auf **helfen** die Version im rechten Bereich angezeigt. Beachten Sie, dass Sie Visual Studio 2010-Tools für Office-Laufzeit zu installieren, bevor Sie das Excel-Add-in installieren müssen.  
  
6.  (Optional) Erstellen Sie ein Konto mit [Windows Azure Marketplace](https://datamarket.azure.com/). Eine der Aufgaben in diesem Tutorial benötigen Sie ein **Azure Marketplace** (ursprünglich die Bezeichnung **Data Market**) Konto. Sie können diese Aufgabe überspringen und mit der folgenden Aufgabe fortfahren.  
  
7.  Laden Sie die Datei Suppliers.xls aus [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=271504).  
  
8.  DQS lässt nicht zu exportieren, die Bereinigung- oder abgleichsergebnisse in eine Excel-Datei bei Verwendung von **64-Bit-Version von Excel**. Es handelt sich um ein bekanntes Problem. Führen Sie folgende Schritte aus, um dieses Problem zu umgehen:  
  
    1.  Führen Sie **DQLInstaller.exe – upgrade**. Wenn Sie z. B. die Standardinstanz von SQL Server installiert haben, steht die Datei DQSInstaller.exe in der Regel unter C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn zur Verfügung. Doppelklicken Sie auf die Datei DQSInstaller.exe.  
  
    2.  In **Konfigurations-Manager für Master Data Services**, klicken Sie auf **Datenbank auswählen**, wählen Sie die vorhandene **MDS** Datenbank, und klicken Sie dann auf **Upgrade**.  
  
## <a name="lessons"></a>Lektionen  
  
|Lektion|Kurze Beschreibung|Für die Bearbeitung voraussichtlich benötigte Zeit (in Minuten)|  
|------------|-----------------------|------------------------------------------------|  
|[Lektion 1: Erstellen der DQS-Wissensdatenbank ' Suppliers '](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)|In dieser Lektion erstellen Sie eine DQS-Wissensdatenbank namens **Lieferanten**.|60|  
|[Lektion 2: Bereinigung von Lieferantendaten mithilfe der Wissensdatenbank ' Suppliers '](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)|In dieser Lektion erstellen und führen Sie ein DQS-Projekt, um die Lieferantendaten in einer Excel-Datei mit bereinigen die **Lieferanten** Wissensdatenbank, die Sie in der ersten Lektion erstellt haben.|45|  
|[Lektion 3: Abgleich von Daten zu entfernen, um Duplikate aus der Lieferantenliste](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)|In dieser Lektion erstellen Sie ein DQS-Projekt, um einen Abgleich auszuführen und so Duplikate in der bereinigten Lieferantenliste zu identifizieren und daraus zu entfernen.|45|  
|[Lektion 4: Speichern von Lieferantendaten in MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)|In dieser Lektion Sie die bereinigten und abgeglichenen Lieferantendaten zu Master Data Services (MDS) mit Hochladen der **MDS-Add-in für Excel**.|45|  
|[Lesson 5: Automatisierung der Bereinigung und Abgleich mit SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)|In dieser Lektion erstellen Sie eine SSIS-Lösung, die Eingabedaten mithilfe von DQS bereinigt, die bereinigten Daten abgleicht, um Duplikate zu entfernen, und die bereinigten und abgeglichenen Daten automatisch in MDS speichert.|75|  
  
## <a name="next-steps"></a>Nächste Schritte  
 Um das Lernprogramm zu starten, gehen Sie zur ersten Lektion: [Lektion 1: Erstellen der DQS-Wissensdatenbank ' Suppliers '](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md).  
  
  
