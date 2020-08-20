---
description: Diagnosedatensätze
title: Diagnosedaten Sätze | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1b407ef1f8664191a16f54942f42f4088824517c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499921"
---
# <a name="diagnostic-records"></a>Diagnosedatensätze
Jeder Umgebung, jeder Verbindung, jeder Anweisung und jedem Deskriptorhandle sind *Diagnosedaten Sätze*zugeordnet. Diese Datensätze enthalten Diagnoseinformationen zur letzten Funktion mit dem Namen, die ein bestimmtes Handle verwendet haben. Die Datensätze werden nur ersetzt, wenn eine andere Funktion mit diesem Handle aufgerufen wird. Es gibt keine Beschränkung für die Anzahl der Diagnosedaten Sätze, die zu einem beliebigen Zeitpunkt gespeichert werden können.  
  
 Es gibt zwei Arten von Diagnosedaten Sätzen: einen *Header Daten Satz* und NULL oder mehr *Statusdaten Sätze*. Der Header Daten Satz ist Datensatz 0. die Statusdaten Sätze sind die Datensätze 1 und höher. Diagnosedaten Sätze bestehen aus einer Reihe separater Felder, die sich für den Header Daten Satz und die Statusdaten Sätze unterscheiden. Außerdem können ODBC-Komponenten eigene Diagnosedaten Satz Felder definieren.  
  
 Obwohl die Diagnosedaten Sätze als Strukturen betrachtet werden können, ist es nicht erforderlich, dass Sie tatsächlich Strukturen sind. die Art und Weise, wie ein Treiber die Diagnoseinformationen speichert, ist Treiber spezifisch.  
  
 Felder in Diagnosedaten Sätzen werden mit **SQLGetDiagField**abgerufen. Die Felder SQLSTATE, Native Error Number und Diagnostic Message der Statusdaten Sätze können mit einem einzelnen-Befehl mit **SQLGetDiagRec**abgerufen werden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Headerdatensatz](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Statusdatensätze](../../../odbc/reference/develop-app/status-records.md)
