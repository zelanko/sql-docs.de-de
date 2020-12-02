---
description: Extrahieren von Daten mithilfe der XML-Quelle
title: Extrahieren von Daten mithilfe der XML-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], XML
- XML source [Integration Services]
ms.assetid: 5d5be54c-2b7e-4957-9193-c5ea5c5d6d15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f3cd306d2cf6097fdb5e178f92e41d45de198783
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96127171"
---
# <a name="extract-data-by-using-the-xml-source"></a>Extrahieren von Daten mithilfe der XML-Quelle

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Um eine XML-Quelle hinzuzufügen und zu konfigurieren, muss das Paket bereits mindestens einen Datenflusstask enthalten.  
  
### <a name="to-extract-data-using-an-xml-source"></a>So extrahieren Sie Daten mithilfe einer XML-Quelle  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus **Toolbox** die XML-Quelle auf die Entwurfsoberfläche.  
  
4.  Doppelklicken Sie auf die XML-Quelle.  
  
5.  Wählen Sie im Bereich **Quellen-Editor für XML** auf der Seite **Verbindungs-Manager** einen Datenzugriffsmodus aus:  
  
    -   Für den Zugriffsmodus **XML-Dateispeicherort** klicken Sie auf **Durchsuchen** , und suchen Sie den Ordner, der die XML-Datei enthält.  
  
    -   Für den Zugriffsmodus **XML-Datei aus Variable** wählen Sie die benutzerdefinierte Variable aus, die den Pfad der XML-Datei enthält.  
  
    -   Für den Zugriffsmodus **XML-Daten aus Variable** wählen Sie die benutzerdefinierte Variable aus, die die XML-Daten enthält.  
  
    > [!NOTE]  
    >  Die Variablen müssen im Bereich des Datenflusstasks definiert werden, der die XML-Quelle enthält, oder im Bereich des Pakets. Darüber hinaus muss die Variable einen Zeichenfolgen-Datentyp aufweisen.  
  
6.  Aktivieren Sie optional das Kontrollkästchen **Inlineschema verwenden** , um anzuzeigen, dass das XML-Dokument Schemainformationen enthält.  
  
7.  Um ein externes XSD-Schema (XML Schema Definition Language) für die XML-Datei anzugeben, führen Sie eine der folgenden Aktionen aus:  
  
    -   Klicken Sie auf **Durchsuchen** , um eine vorhandene XSD-Datei zu suchen.  
  
    -   Klicken Sie auf **XSD-Code generieren** , um XSD-Code von der XML-Datei zu erstellen.  
  
8.  Um die Namen von Ausgabespalten zu aktualisieren, klicken Sie auf **Spalten** , und bearbeiten Sie die Werte in der Liste **Ausgabespalte** .  
  
9. Klicken Sie auf **Fehlerausgabe**, um die Fehlerausgabe zu konfigurieren. Weitere Informationen finden Sie unter [Debugging Data Flow](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
10. Klicken Sie auf **OK**.  
  
11. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Quelle](../../integration-services/data-flow/xml-source.md)   
 [SQL Server Integration Services-Transformationen](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](../../integration-services/data-flow/integration-services-paths.md)   
 [Datenflusstask](../../integration-services/control-flow/data-flow-task.md)  
  
  
