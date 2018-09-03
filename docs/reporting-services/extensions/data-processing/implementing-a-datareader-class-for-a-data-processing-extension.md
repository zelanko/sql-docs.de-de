---
title: Implementieren einer DataReader-Klasse für Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5ab7855a916a1a1dbd6d75fad9004c656e24641f
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43266609"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>Implementieren einer DataReader-Klasse für Datenverarbeitungserweiterungen
  Mithilfe des **DataReader**-Objekts kann ein Client einen schreibgeschützten Vorwärtsdatenstrom von einer Datenquelle empfangen. Ergebnisse werden bei der Ausführung der Abfrage zurückgegeben und im Netzwerkpuffer auf dem Client gespeichert, bis Sie sie unter Verwendung der **Read**-Methode der **DataReader**-Klasse anfordern. Implementieren Sie <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> und optional <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>, um eine **DataReader**-Klasse zu erstellen. Die Verwendung eines **DataReader**-Objekts erhöht die Anwendungsleistung, da die Daten sofort bei Verfügbarkeit abgerufen werden, statt auf die gesamten Ergebnisse der Abfrage zu warten, und da (standardmäßig) immer nur eine Zeile im Speicher gespeichert wird. So wird der Systemverwaltungsaufwand reduziert.  
  
 Nachdem Sie eine Instanz der **Command**-Klasse erstellt haben, legen Sie ein **DataReader**-Objekt an, indem Sie **Command.ExecuteReader** aufrufen, um Zeilen von der Datenquelle abzurufen. Die **DataReader**-Implementierung muss über zwei grundlegende Funktionen verfügen: Vorwärtszugriff auf die Resultsets, die durch die Ausführung eines Befehls abgerufen wurden, und Zugriff auf die Spaltentypen, Namen und Werte innerhalb jeder Zeile. Clients verwenden die **Read**-Methode des **DataReader**-Objekts, um eine Zeile aus den Ergebnissen der Abfrage abzurufen.  
  
 Im Berichts-Designer werden mithilfe des **DataReader**-Objekts eine Liste der Felder sowie Schemainformationen zur Ergebnisreihe abgerufen. Hierzu müssen die Methoden **GetName**, **GetValue**, **GetFieldType,** und **GetOrdinal** der <xref:Microsoft.ReportingServices.DataProcessing.IDataReader>-Schnittstelle implementiert werden.  
  
 Mit der <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>-Schnittstelle können Sie bestimmte Aggregationsinformationen über das Resultset angeben. Eine Beispiel-**DataReader**-Klassenimplementierung finden Sie unter [SQL Server Reporting Services Product Samples (SQL Server Reporting Services-Produktbeispiele)](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterungen für Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
