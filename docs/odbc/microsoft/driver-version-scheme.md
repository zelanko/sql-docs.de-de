---
title: Treiberversionsschema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6c76b1a931101fce366cc6d3b20d4aa74de23e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806528"
---
# <a name="driver-version-scheme"></a>Treiberversionsschema
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Die folgende Tabelle enthält alle veröffentlichte Versionen von Microsoft ODBC-Treiber für Oracle.  
  
|Treiberversion|Buildnummer|Verfügbarkeitsverlauf|  
|--------------------|------------------|--------------------------|  
|1,0|2.00.6235|Visual C++ 4.2- und Visual Basic 5.0, Enterprise Edition|  
|2.0|2.73.7269|Visual Studio 97 und MDAC 1,5 a|  
|2.0 aktualisiert|2.73.7283.01|IIS 4.0|  
|2.0 aktualisiert|2.73.7283.03|MDAC 1.5b und 1.5-c|  
|2.0 aktualisiert|2.73.7356|ODBC 3.5-SDK|  
|2.5|2.573.2927|MDAC 2.0 und Visual Studio 6.0|  
|2.5 aktualisiert|2.573.3513|SQLServer 7.0<br /><br /> SQL Server 6.5 SP5|  
  
 Build 2.00.6235 (Version 1) war die erste Version von Microsoft ODBC-Treiber für Oracle. Nach der Veröffentlichung der ersten Version wurde eine neue Namenskonvention übernommen.  
  
 Beispielsweise können 2.73.7283.03 in die folgenden unterschiedlichen Komponenten unterteilt werden:  
  
-   2 = die Versionsnummer.  
  
-   73 = die Version des Oracle-Server, die für das der Treiber entwickelt wurde.  
  
-   7283.03 = die Buildnummer des Treibers.  
  
> [!NOTE]  
>  Mit Version 2.573.2973, die Benennungskonvention hat dazu geführt, um Verwirrung zu geben, dass 2.573 eine frühere Version als 2,73, aber jeder Teil die Nummer des Builds einzeln angesehen werden. Die Anzahl 573 ist größer als 73, daher ist es eine neuere Version. Darüber hinaus gibt "2.5" Versionsnummer des Treibers an.
