---
title: Suchen der Berichtsdefinitions-Schemaversion (SSRS) | Microsoft-Dokumentation
ms.date: 06/06/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- XML schemas [Reporting Services]
- Report Definition Language, XML schema
- schemas [Reporting Services]
ms.assetid: 67954419-1b61-4481-a3b9-23b4ba7a5624
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 129fcb8e1533162560b88e9400c68c7c863be119
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66826840"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a>Suchen der Berichtsdefinitions-Schemaversion (SSRS)

In einer Berichtsdefinitionsdatei ist der RDL-Namespace für die Version des Berichtsdefinitionsschemas angegeben, das zur Überprüfung der RDL-Datei verwendet wird. Wenn Sie eine RDL-Datei öffnen, in einer berichterstellungsumgebung wie dem Berichts-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], Visual Studio oder Berichts-Generator. Wenn der Bericht für einen vorherigen Namespace erstellt wurde, eine Sicherungsdatei wird automatisch erstellt, und der Bericht wird auf den aktuellen Namespace aktualisiert. Wenn Sie die aktualisierte Berichtsdefinition speichern, haben Sie die konvertierte RDL-Datei gespeichert. Dies ist die einzige Möglichkeit, eine Berichtsdefinition zu aktualisieren. Die Berichtsdefinition selbst wird auf einem Berichtsserver nicht aktualisiert. Der kompilierte Bericht wird auf einem Berichtsserver aktualisiert. Weitere Informationen finden Sie unter [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md).  
  
## <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a>Vorgehensweise: Identifizieren der RDL-Schemaversion eines Berichts  
  
1. Öffnen Sie die RDL-Berichtsdatei in einer Anwendung wie Editor oder XML Notepad, in der Sie die XML anzeigen können.  
  
     Das XML-Berichtselement gibt den Schemanamespace an. Zum Beispiel gibt das folgende Berichtselement den Namespace für den Berichts-Designer und den Namespace für die Berichtsdefinition an.  
  
    ``` XML 
    <Report xmlns:rd="http://schemas.microsoft.com/SQLServer/reporting/reportdesigner" xmlns="http://schemas.microsoft.com/sqlserver/reporting/2016/01/reportdefinition" xmlns:df="http://schemas.microsoft.com/sqlserver/reporting/2016/01/reportdefinition/defaultfontfamily" MustUnderstand="df">  
    ```  
  
     Der letzte berichtsdefinitionsnamespace ist 2016. Allerdings ist die neueste veröffentlichte berichtsdefinitionsnamespace 2010, die von der folgenden URL angegeben: `https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition`...
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a>Vorgehensweise: Identifizieren der RDL-Schemaversion des Berichts-Designers  
  
1.  Öffnen Sie ein neues Projekt. Die Version des ausgewählten Projekts bestimmt die Version des RDL-Schemas. In SQL Server werden mehrere Schemaversionen unterstützt. Weitere Informationen finden Sie unter [Bereitstellung und Versionsunterstützung in SQL Server Data Tools](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**. Das Dialogfeld **Neues Element hinzufügen** wird geöffnet.  
  
3.  Klicken Sie im Bereich **Vorlagen** auf **Bericht**.  
  
4.  Geben Sie im Feld **Name**einen Berichtsnamen ein, oder übernehmen Sie den Standardnamen.  
  
5.  Klicken Sie auf **Hinzufügen**. Der Berichts-Designer öffnet in der Entwurfsansicht einen neuen leeren Bericht.  
  
6.  Klicken Sie im Menü **Ansicht** auf **Code**. Die Berichtsdefinition wird als XML-Datei angezeigt.  
  
    Das XML-Berichtselement gibt den Schemanamespace an. Zum Beispiel gibt das folgende Berichtselement den Namespace für den Berichts-Designer und den Namespace für die Berichtsdefinition an.  
  
    ``` XML 
    <Report xmlns:rd="http://schemas.microsoft.com/SQLServer/reporting/reportdesigner" xmlns="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition" xmlns:df="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition/defaultfontfamily" MustUnderstand="df">  
    ```  
  
     Der Berichtsdefinitionsnamespace wird von der folgenden URL angegeben: `https://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition`  
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a>Vorgehensweise: Identifizieren der RDL-Schemaversion auf dem Berichtsserver  
  
-   Geben Sie im Webportal die URL für den Berichtsserver ein. Die folgende URL gibt z. B. einen Berichtsserver auf dem lokalen Computer an:  
  
     `https://localhost/reportserver/reportdefinition.xsd`  
  
     Die XSD-Datei wird im Browser geöffnet.  
  
     Das XML-Schemaelement gibt den Schemanamespace an. Das folgende Schemaelement gibt beispielsweise drei Namespaces an: den targetNamespace-Verweis, der intern von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]verwendet wird, den XSD-Verweis für das Schema selbst (XSD) und die Berichtsdefinitionsreferenz.  *Jahr* stellt das Jahr des Schemas der Bericht dar. Z. B. 2010 oder 2016.
  
    ``` XML  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition" targetNamespace="http://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition" elementFormDefault="qualified">  
    ```  
  
     Der Berichtsdefinitionsnamespace wird von der folgenden URL angegeben: `https://schemas.microsoft.com/sqlserver/reporting/*year*/01/reportdefinition`  

## <a name="next-steps"></a>Nächste Schritte
[Aktualisieren von Berichten](../../reporting-services/install-windows/upgrade-reports.md)   
[Report Definition Language (Berichtsdefinitionssprache)](../../reporting-services/reports/report-definition-language-ssrs.md)   

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
