---
title: Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC]
- data sources [ODBC], about data sources
ms.assetid: 4ae44fa2-0b9b-4e19-ab45-c1dc93b68406
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b7e464963471b0cad41c5b93d50507d0fa9bf96
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306511"
---
# <a name="data-sources"></a>Projektmappen-Explorer
Eine *Datenquelle* ist einfach die Quelle der Daten. Dabei kann es sich um eine Datei, eine bestimmte Datenbank in einem DBMS oder sogar um einen livedatenfeed handeln. Die Daten befinden sich möglicherweise auf demselben Computer wie das Programm oder auf einem anderen Computer in einem Netzwerk. Beispielsweise kann eine Datenquelle ein Oracle-DBMS sein, das unter einem Betriebssystem mit Betriebssystem/2® ausgeführt wird, auf das Novell® NetWare zugreift. ein IBM DB2-DBMS, auf das über ein Gateway zugegriffen wird; eine Auflistung von xbase-Dateien in einem Serververzeichnis. oder eine lokale Microsoft® Access-Datenbankdatei.  
  
 Der Zweck einer Datenquelle besteht darin, alle technischen Informationen zu erfassen, die für den Zugriff auf die Daten erforderlich sind, den Treiber Namen, die Netzwerkadresse, die Netzwerk Software usw., um Sie für den Benutzer auszublenden. Der Benutzer sollte in der Lage sein, eine Liste mit Gehalts-, Bestands-und Personalinformationen zu sehen, Gehaltsdaten aus der Liste auszuwählen und die Anwendung mit den Gehaltsdaten zu verbinden, ohne zu wissen, wo sich die Abrechnungsdaten befinden oder wie die Anwendung zu ihr gelangt ist.  
  
 Der Begriff " *Datenquelle* " sollte nicht mit ähnlichen Begriffen verwechselt werden. In diesem Handbuch bezieht sich *DBMS* oder die *Datenbank* auf ein Datenbankprogramm oder eine-Engine. Es wird ein weiterer Unterschied zwischen *Desktop Datenbanken hergestellt,* die auf PCs ausgeführt werden und häufig in der vollständigen SQL-und Transaktionsunterstützung fehlen, sowie auf *Server Datenbanken,* die in einer Client-/Serversituation ausgeführt werden sollen und durch eine eigenständige Datenbank-Engine und umfassende Unterstützung für SQL und Transaktionen gekennzeichnet sind. *Datenbank* bezieht sich auch auf eine bestimmte Sammlung von Daten, z. b. eine Sammlung von xbase-Dateien in einem Verzeichnis oder eine Datenbank auf SQL Server. Dies entspricht im Allgemeinen dem Begriff *Catalog,* der an anderer Stelle in diesem Handbuch verwendet wird, oder dem Begriff *Qualifizierer* in früheren Versionen von ODBC.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Typen von Datenquellen](../../odbc/reference/types-of-data-sources.md)  
  
-   [Verwenden von Datenquellen](../../odbc/reference/using-data-sources.md)  
  
-   [Beispiel für Datenquellen](../../odbc/reference/data-source-example.md)
