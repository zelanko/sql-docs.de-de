---
description: Schemaansichten
title: Schema Sichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 34e1b52b5e96b5fedb964e53f14a7b554d12aa05
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429072"
---
# <a name="schema-views"></a>Schemaansichten
Eine Anwendung kann Metadateninformationen aus dem DBMS abrufen, indem Sie entweder ODBC-Katalog Funktionen oder INFORMATION_SCHEMA Sichten aufruft. Die Sichten werden durch den ANSI SQL-92-Standard definiert.  
  
 Wenn Sie vom DBMS und dem Treiber unterstützt werden, bieten die INFORMATION_SCHEMA Sichten eine leistungsfähigere und umfassendere Methode zum Abrufen von Metadaten, die von den ODBC-Katalog Funktionen bereitgestellt werden. Eine Anwendung kann eine eigene benutzerdefinierte **Select** -Anweisung für eine dieser Sichten ausführen, Ansichten verknüpfen oder eine Union für Ansichten ausführen. Wenn Sie ein höheres Hilfsprogramm und eine größere Anzahl von Metadaten anbieten, werden INFORMATION_SCHEMA Sichten nicht häufig vom DBMS unterstützt. Dies kann sich ändern, wenn mehr DBMSs und Treiber die Kompatibilität mit SQL-92 erzielen.  
  
 Um zu ermitteln, welche Sichten unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit der SQL_INFO_SCHEMA_VIEWS-Option auf. Zum Abrufen von Metadaten aus einer unterstützten Ansicht führt die Anwendung eine **Select** -Anweisung aus, die die erforderlichen Schema Informationen angibt.
