---
title: Implementieren einer Command-Klasse für Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e415d9498c624aa3dcea443f2cdc3641dd7c8491
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "63193943"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>Implementieren einer Command-Klasse für Datenverarbeitungserweiterungen
  Das **Command**-Objekt formuliert eine Anforderung und übergibt sie an die Datenquelle. Der Befehlstext kann viele verschiedene syntaktische Formate haben, einschließlich Text und XML. Wenn Ergebnisse zurückgegeben werden, gibt das **Command**-Objekt die Ergebnisse als **DataReader**-Objekt zurück.  
  
 Um eine **Command**-Klasse zu erstellen, implementieren Sie <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>. Implementieren Sie die <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>-Methode, um ein Resultset als **DataReader**-Objekt zurückzugeben. Die <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>-Methode Ihrer **Command**-Klasse sollte eine Implementierung enthalten, die eine <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior>-Enumeration als Argument verwendet. Wenn Sie die Datenverarbeitungserweiterungen im Berichts-Designer bereitstellen, geben Sie eine Implementierung an, die einen <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly>-Fall in der Methode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> behandelt. Eine Schema-Only-Implementierung wird verwendet, um dem Berichts-Designer eine Felderliste zur Verfügung zu stellen. Das **DataReader**-Objekt, das von der Methode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> zurückgegeben wurde, muss Typen- und Namensdaten für die Felder oder Spalten in Ihrem Resultset enthalten.  
  
 Optional kann die **Command**-Klasse <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> implementieren. Mithilfe dieser Oberfläche kann eine Implementierungsklasse eine Abfrage analysieren und eine Parameterliste in der Abfrage zurückgeben. Die Funktionen der <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>-Schnittstelle werden nur im Berichts-Designer verwendet. Wenn Sie <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> implementieren, können Benutzer des Berichts-Designers zur Eingabe von Parametern aufgefordert werden, wenn ein Bericht im Vorschaumodus ausgeführt wird. Außerdem können Sie die Parameter im Dialogfeld **Dataset** auf der Registerkarte **Parameter** anzeigen.  
  
> [!NOTE]  
>  Sie sollten <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> nicht implementieren, wenn die benutzerdefinierte Datenverarbeitungserweiterung keine Parameter unterstützt.  
  
 Eine Beispiel-**Command**-Klassenimplementierung finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen für Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
