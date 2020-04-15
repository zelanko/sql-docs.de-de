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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306511"
---
# <a name="data-sources"></a>Projektmappen-Explorer
Eine *Datenquelle* ist einfach die Quelle der Daten. Dabei kann es sich um eine Datei, eine bestimmte Datenbank auf einem DBMS oder sogar um einen Live-Datenfeed handelt. Die Daten befinden sich möglicherweise auf demselben Computer wie das Programm oder auf einem anderen Computer irgendwo in einem Netzwerk. Eine Datenquelle kann z. B. ein Oracle DBMS sein, das auf einem Betriebssystem für OS/2® ausgeführt wird und auf das Novell® Netware. ein IBM DB2 DBMS, auf das über ein Gateway zugegriffen wird; eine Sammlung von Xbase-Dateien in einem Serververzeichnis; oder eine lokale Microsoft® Access-Datenbankdatei.  
  
 Der Zweck einer Datenquelle besteht darin, alle technischen Informationen, die für den Zugriff auf die Daten erforderlich sind - Den Treibernamen, die Netzwerkadresse, die Netzwerksoftware usw. - an einem einzigen Ort zu sammeln und vor dem Benutzer zu verbergen. Der Benutzer sollte in der Lage sein, eine Liste zu betrachten, die Lohn-, Bestands- und Personalabrechnung enthält, die Option Lohnabrechnung aus der Liste auswählen und die Anwendung mit den Lohndaten verbinden lassen, ohne zu wissen, wo sich die Lohndaten befinden oder wie die Anwendung dazu gelangt ist.  
  
 Der Begriff *Datenquelle* sollte nicht mit ähnlichen Begriffen verwechselt werden. In diesem Handbuch bezieht sich *DBMS* oder *Datenbank* auf ein Datenbankprogramm oder -modul. Eine weitere Unterscheidung wird zwischen *Desktopdatenbanken,* die für die Ausführung auf PCs entwickelt wurden und denen häufig keine vollständige SQL- und Transaktionsunterstützung fehlt, und *Serverdatenbanken,* die für die Ausführung in einer Client-/Server-Situation entwickelt wurden und durch eine eigenständige Datenbank-Engine und umfangreiche SQL- und Transaktionsunterstützung gekennzeichnet sind. *Datenbank* bezieht sich auch auf eine bestimmte Sammlung von Daten, z. B. eine Sammlung von Xbase-Dateien in einem Verzeichnis oder eine Datenbank auf SQL Server. Es entspricht im Allgemeinen dem Begriff *Katalog,* der an anderer Stelle in diesem Handbuch verwendet wird, oder dem Begriff *Qualifizierer* in früheren Versionen von ODBC.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Typen von Datenquellen](../../odbc/reference/types-of-data-sources.md)  
  
-   [Verwenden von Datenquellen](../../odbc/reference/using-data-sources.md)  
  
-   [Beispiel für Datenquellen](../../odbc/reference/data-source-example.md)
