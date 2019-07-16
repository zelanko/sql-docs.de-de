---
title: DiagnoseDatensätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 90133b4a18876c52b9b6b6bffbe4c8c02c953e07
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039881"
---
# <a name="diagnostic-records"></a>Diagnosedatensätze
Jede Umgebung zugeordnet, Verbindung, -Anweisung und Deskriptorhandles sind *DiagnoseDatensätze*. Dieser Datensatz enthält Diagnoseinformationen über die letzte Funktion wird aufgerufen, die ein bestimmtes Handle verwendet. Nur, wenn eine andere Funktion mit diesem Handle aufgerufen wird, werden die Datensätze ersetzt. Es gibt keine Beschränkung der Anzahl der DiagnoseDatensätze, die zu jedem Zeitpunkt gespeichert werden können.  
  
 Es gibt zwei Arten von Diagnosedatensätzen: eine *Headerdatensatz* und NULL oder mehr *Statusdatensätze*. Der Headerdatensatz ist Datensatz 0; die Statusdatensätze sind Datensätze 1 und höher. DiagnoseDatensätze umfassen eine Reihe von separaten Feldern, die für den Headerdatensatz und die Statusdatensätze unterschiedlich sind. ODBC-Komponenten können außerdem eigene diagnosedatensatzfelder definieren.  
  
 DiagnoseDatensätze als Strukturen betrachtet werden können, zwar gibt es nicht erforderlich, damit sie tatsächlich Strukturen werden; wie ein Treiber für die Diagnoseinformationen speichert ist treiberspezifisch.  
  
 Feldern in Diagnosedatensätzen werden abgerufen, mit **SQLGetDiagField**. Der SQLSTATE, systemeigener Fehlernummer und diagnosemeldung Felder der Statusdatensätze mit einem einzigen Aufruf abgerufen werden können **SQLGetDiagRec**.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Headerdatensatz](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Statusdatensätze](../../../odbc/reference/develop-app/status-records.md)
