---
title: Dynamische Ablauf Verfolgung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8cbd2dbae4f4b437f45845ce2791f4a9b0aa8c8b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305766"
---
# <a name="dynamic-tracing"></a>Dynamische Ablaufverfolgung
Die Ablauf Verfolgung kann jederzeit in einer Anwendungs Laufzeit aktiviert oder deaktiviert werden. Dadurch kann eine Anwendung eine beliebige Anzahl von Funktionsaufrufen verfolgen.  
  
 Die Variable **odbcsharedtraceflag** ist so festgelegt, dass die Ablauf Verfolgung dynamisch aktiviert wird. Diese Variable wird von allen laufenden Kopien des Treiber-Managers gemeinsam genutzt. Wenn von einer Anwendung diese Variable festgelegt wird, wird die Ablauf Verfolgung für alle derzeit laufenden ODBC-Anwendungen aktiviert. Um die Ablauf Verfolgung zu deaktivieren, wenn die dynamische Ablauf Verfolgung aktiviert ist, ruft eine Anwendung **SQLSetConnectAttr** auf, um SQL_ATTR_TRACE auf SQL_TRACE_OFF festzulegen. Mit diesem Befehl wird die Ablauf Verfolgung nur für diese Anwendung deaktiviert. Anwendungen, die mit odbc32. lib verknüpft sind, können die Verwendung dieser Variablen ändern. Ablauf Verfolgungs Daten können in einem echt Zeitfenster anstelle der Ablauf Verfolgungs Datei angezeigt werden, die nach der ODBC-Sitzung geöffnet werden muss. Sie können dem Bildschirm einer Anwendung Steuerelemente hinzufügen, um die Ablauf Verfolgung zu aktivieren oder zu deaktivieren.  
  
 Die Ablauf Verfolgungs-dll, die mit ODBC 3 *. x* ausgeliefert wurde, ist nicht Thread sicher. Es ist nicht garantiert, dass die Protokolldatei ordnungsgemäß geschrieben wird, wenn die globale Ablauf Verfolgung aktiviert ist (die Variable " **odbcsharedtraceflag** " ist festgelegt) und mehrere Anwendungen gleichzeitig in die Ablauf Verfolgungs Datei schreiben. Diese Bedingung gibt keinen Fehler zurück.
