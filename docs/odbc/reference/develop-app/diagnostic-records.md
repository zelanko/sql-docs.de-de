---
title: Diagnosedatensätze | Microsoft Docs
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
ms.openlocfilehash: b564f2837bc76e04011170e191d00c08d10c119d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305181"
---
# <a name="diagnostic-records"></a>Diagnosedatensätze
Jeder Umgebung sind Verbindung, Anweisung und Deskriptorhandle *Diagnosedatensätze*zugeordnet. Diese Datensätze enthalten Diagnoseinformationen über die letzte Funktion, die aufgerufen wurde, die ein bestimmtes Handle verwendet hat. Die Datensätze werden nur ersetzt, wenn eine andere Funktion mit diesem Handle aufgerufen wird. Die Anzahl der Diagnosedatensätze, die gleichzeitig gespeichert werden können, ist unbegrenzt.  
  
 Es gibt zwei Arten von Diagnosedatensätzen: einen *Headerdatensatz* und null oder mehr *Statusdatensätze*. Der Headerdatensatz ist Datensatz 0; die Statusdatensätze sind Datensätze 1 und höher. Diagnosedatensätze bestehen aus einer Reihe separater Felder, die sich für den Kopfdatensatz und die Statusdatensätze unterscheiden. Darüber hinaus können ODBC-Komponenten eigene Diagnosesatzfelder definieren.  
  
 Obwohl Diagnoseaufzeichnungen als Strukturen betrachtet werden können, ist es nicht erforderlich, dass sie tatsächlich Strukturen sind; Wie ein Treiber die Diagnoseinformationen speichert, ist treiberspezifisch.  
  
 Felder in Diagnosedatensätzen werden mit **SQLGetDiagField**abgerufen. Die SQLSTATE-, systemeigenen Fehlernummer- und Diagnosemeldungsfelder von Statusdatensätzen können in einem einzigen Aufruf mit **SQLGetDiagRec**abgerufen werden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Headerdatensatz](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Statusdatensätze](../../../odbc/reference/develop-app/status-records.md)
