---
title: Enterprise Information Management mit SSIS, MS und DQS zusammen [Tutorial] | Microsoft Docs
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
ms.openlocfilehash: 29ed5816a3a5fc0af6c5a4ac144557933e3e1a5f
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487719"
---
# <a name="enterprise-information-management-using-ssis-mds-and-dqs-together-tutorial"></a>Enterprise Information Management mit SSIS, MDS und DQS [Lernprogramm]
  Das Verwalten von Informationen in einem Unternehmen schließt in der Regel die Integration von Daten im gesamten Unternehmen und darüber hinaus ein, außerdem Bereinigen der Daten, Abgleichen der Daten zum Entfernen aller Duplikate, Standardisieren der Daten, Erweitern der Daten, Sicherstellen, dass die Daten gesetzliche und Kompatibilitätsanforderungen erfüllen, und Speichern der Daten an einem zentralen Ort mit allen erforderlichen Sicherheitseinstellungen.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] stellt alle für eine effektive Enterprise Information Management (EIM)-Lösung benötigten Komponenten in einem einzigen Produkt bereit. Folgende Schlüsselkomponenten bieten Unterstützung bei der Erstellung einer EIM-Lösung:  
  
-   SQL Server Integration Services  
  
-   SQL Server Data Quality Services  
  
-   SQL Server Master Data Services  
  
 SQL Server Integration Services (SSIS) stellt eine leistungsstarke, erweiterbare Plattform für das Integrieren von Daten aus verschiedenen Quellen in einer umfassenden Lösung zum Extrahieren, Transformieren und Laden von Daten (ETL-Lösung) bereit, die Geschäftsworkflows, ein Data Warehouse oder die Masterdatenverwaltung unterstützt. Im Thema [Integration Services Overview](https://msdn.microsoft.com/library/ms141263\(SQL.105\).aspx) finden Sie eine kurze Übersicht über typische Verwendungen von SSIS.  
  
 SQL Server Data Quality Services (DQS) ermöglicht es Ihnen, Daten zu bereinigen, abzugleichen, zu standardisieren und zu erweitern, sodass Sie zuverlässige Informationen für Business Intelligence, ein Data Warehouse und Transaktionsverarbeitungs-Arbeitsauslastungen übermitteln können. Weitere Informationen zum Geschäftlichen von DQS und zur Behebung der Anforderungen von DQS finden Sie unter [Einführung in Data Quality Services.](https://msdn.microsoft.com/library/ff877917.aspx)  
  
 SQL Server Master Data Services (MDS) bietet einen zentralen Datenhub, der sicherstellt, dass die Integrität der Informationen und die Einheitlichkeit der Daten in verschiedenen Anwendungen konstant sind. Im Thema [Master Data Services Overview](../master-data-services/master-data-services-overview-mds.md) finden Sie kurze Beschreibungen wichtiger Features von MDS.  
  
 Eine umfassende Anleitung zum Implementieren einer EIM-Lösung mithilfe dieser Microsoft EIM-Technologien finden Sie unter [Bereinigen und Abgleich von Masterdaten mithilfe](https://msdn.microsoft.com/library/hh403491.aspx) von EIM Technologies, um [Gemeinsamkeits- und Unternehmensinformationsmanagement (EIM) zu sehen: Zusammenführen von SSIS-, DQS- und MDS-Videos](https://go.microsoft.com/fwlink/?LinkId=258672) für eine coole Demonstration eines EIM-Szenarios.  
  
 In diesem Lernprogramm erfahren Sie, wie Sie SSIS, MDS und DQS zusammen verwenden, um eine Enterprise Information Management (EIM)-Beispiellösung zu implementieren. Zunächst erstellen Sie mithilfe von DQS eine Wissensdatenbank, die Informationen zu den Daten (Metadaten) enthält. Dann bereinigen Sie die Daten in einer Excel-Datei anhand der Wissensdatenbank und gleichen die Daten ab, um Duplikate in den Daten zu identifizieren und zu entfernen. Als Nächstes verwenden Sie das MDS-Add-In für Excel, um die bereinigten und abgeglichenen Daten in MDS hochzuladen. Dann automatisieren Sie den gesamten Prozess, indem Sie eine SSIS-Lösung verwenden. Die SSIS-Lösung in diesem Tutorial liest die Eingabedaten aus einer Excel-Datei, sie können jedoch auf das Lesen aus verschiedenen Quellen wie Oracle, Teradata, DB2 und Azure SQL-Datenbank erweitert werden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
1.  Microsoft SQL Server 2012 mit den folgenden installierten Komponenten:  
  
    1.  Integration Services (SSIS)  
  
    2.  Master Data Services (MDS)  
  
    3.  Data Quality Services (DQS)  
  
    4.  SQL Server Data Tools  
  
         Weitere Informationen zur Installation des Produkts finden Sie im [SQL Server 2012-Installationshandbuch.](../database-engine/install-windows/installation-for-sql-server.md)  
  
2.  [Konfigurieren Sie MDS mithilfe des Master Data Services-Konfigurations-Managers.](https://msdn.microsoft.com/library/ee633884.aspx)  
  
     Verwenden Sie den Konfigurations-Manager, um eine Master Data Services-Datenbank zu erstellen und zu konfigurieren. Nachdem Sie die MDS-Datenbank erstellt haben, erstellen Sie eine Webanwendung für MDS in einer Website (z. B.: `http://localhost/MDS`), und ordnen Sie die MDS-Datenbank der MDS-Webanwendung zu. Beachten Sie, dass zum Erstellen einer MDS-Webanwendung IIS auf Ihrem Computer installiert sein muss. Weitere Informationen zu den Voraussetzungen für die Konfiguration der MDS-Datenbank und der Webanwendung finden Sie unter [Webanwendungsanforderungen (Master Data Services)](https://msdn.microsoft.com/library/ee633744.aspx) und [Datenbankanforderungen (Master Data Services).](https://msdn.microsoft.com/library/ee633767.aspx)  
  
3.  [Installieren und Konfigurieren von DQS mit Data Quality Server Installer](https://msdn.microsoft.com/library/hh231682.aspx). Klicken Sie auf **Starten**, klicken Sie auf **Alle Programme**, klicken Sie auf Microsoft SQL **Server 2014**, klicken Sie auf **Data Quality Services**, und klicken Sie dann auf Data Quality **Server Installer**.  
  
4.  Microsoft Excel 2010 (32-Bit wird bevorzugt).  
  
5.  Installieren Sie **das Master Data Services-Add-In für Excel** (32-Bit oder 64-Bit basierend auf der Excel-Version auf Ihrem Computer) von [hier](https://www.microsoft.com/download/details.aspx?id=29064). Um die auf Ihrem Computer installierte Excel-Version zu finden, führen Sie **Excel**aus , **klicken** Sie in der Menüleiste auf Datei und klicken Sie auf **Hilfe,** um die Version im rechten Bereich anzuzeigen. Beachten Sie, dass Sie vor der Installation des Excel Add-Ins Visual Studio 2010 Tools für Office-Laufzeit installieren müssen.  
  
6.  (Optional) Erstellen Sie ein Konto bei [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/). Eine der Aufgaben im Tutorial erfordert, dass Sie über ein **Azure Marketplace-Konto** (ursprünglich **Data Market)** verfügen. Sie können diese Aufgabe überspringen und mit der folgenden Aufgabe fortfahren.  
  
7.  Laden Sie die Datei Suppliers.xls aus [dem Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=50426)herunter.  
  
8.  DQS ermöglicht es Ihnen nicht, die Bereinigungs- oder Übereinstimmungsergebnisse in eine Excel-Datei zu exportieren, wenn Sie die **64-Bit-Version von Excel**verwenden. Es handelt sich um ein bekanntes Problem. Führen Sie folgende Schritte aus, um dieses Problem zu umgehen:  
  
    1.  Führen Sie **DQLInstaller.exe -upgrade aus.** Wenn Sie z. B. die Standardinstanz von SQL Server installiert haben, steht die Datei DQSInstaller.exe in der Regel unter C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn zur Verfügung. Doppelklicken Sie auf die Datei DQSInstaller.exe.  
  
    2.  Klicken Sie in **Master Data Services Configuration Manager**auf Datenbank **auswählen**, wählen Sie vorhandene **MDS-Datenbank** aus, und klicken Sie dann auf **Aktualisieren**.  
  
## <a name="lessons"></a>Lektionen  
  
|Lektion|Kurzbeschreibung|Für die Bearbeitung voraussichtlich benötigte Zeit (in Minuten)|  
|------------|-----------------------|------------------------------------------------|  
|[Lektion 1: Erstellen der DQS-Wissensdatenbank „Suppliers“](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)|In dieser Lektion erstellen Sie eine DQS-Wissensdatenbank mit dem Namen **Lieferanten**.|60|  
|[Lektion 2: Bereinigung von Lieferantendaten mithilfe der Wissensdatenbank „Suppliers“](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)|In dieser Lektion erstellen und führen Sie ein DQS-Projekt aus, um die Lieferantendaten in einer Excel-Datei zu bereinigen, indem Sie die **Suppliers** Knowledge Base verwenden, die Sie in der ersten Lektion erstellt haben.|45|  
|[Lektion 3: Abgleich von Daten zur Entfernung von Duplikaten aus der Lieferantenliste](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)|In dieser Lektion erstellen Sie ein DQS-Projekt, um einen Abgleich auszuführen und so Duplikate in der bereinigten Lieferantenliste zu identifizieren und daraus zu entfernen.|45|  
|[Lektion 4: Speichern von Lieferantendaten in MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)|In dieser Lektion laden Sie die bereinigten und übereinstimmenden Lieferantendaten mithilfe des **MDS-Add-Ins für Excel**in Master Data Services (MDS) hoch.|45|  
|[Lektion 5: Automatisierung der Bereinigung und des Abgleich mit SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)|In dieser Lektion erstellen Sie eine SSIS-Lösung, die Eingabedaten mithilfe von DQS bereinigt, die bereinigten Daten abgleicht, um Duplikate zu entfernen, und die bereinigten und abgeglichenen Daten automatisch in MDS speichert.|75|  
  
## <a name="next-steps"></a>Nächste Schritte  
 Um mit dem Tutorial zu beginnen, fahren Sie mit der ersten Lektion fort: [Lektion 1: Erstellen der DQS-Wissensdatenbank für Lieferanten](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md).  
  
  
