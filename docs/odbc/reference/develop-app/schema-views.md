---
title: Schemaansichten | Microsoft Docs
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
ms.openlocfilehash: a1a9e421c4835d35e3c4f3c644e69b8c7601e8e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304251"
---
# <a name="schema-views"></a>Schemaansichten
Eine Anwendung kann Metadateninformationen aus dem DBMS abrufen, indem sie ODBC-Katalogfunktionen aufruft oder INFORMATION_SCHEMA Ansichten verwendet. Die Ansichten werden durch den ANSI SQL-92-Standard definiert.  
  
 Wenn sie vom DBMS und dem Treiber unterstützt werden, bieten die INFORMATION_SCHEMA Ansichten eine leistungsfähigere und umfassendere Möglichkeit zum Abrufen von Metadaten als die ODBC-Katalogfunktionen. Eine Anwendung kann eine eigene benutzerdefinierte **SELECT-Anweisung** für eine dieser Ansichten ausführen, Ansichten beitreten oder eine Union für Ansichten ausführen. Obwohl sie mehr Nutzen und eine größere Auswahl an Metadaten bieten, werden INFORMATION_SCHEMA Ansichten häufig nicht vom DBMS unterstützt. Dies kann sich ändern, wenn mehr DBMS und Treiber die Einhaltung von SQL-92 erreichen.  
  
 Um zu bestimmen, welche Ansichten unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_INFO_SCHEMA_VIEWS auf. Um Metadaten aus einer unterstützten Ansicht abzurufen, führt die Anwendung eine **SELECT-Anweisung** aus, die die erforderlichen Schemainformationen angibt.
