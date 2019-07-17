---
title: Standard-Programmierschnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], programming interface
- programming interface standardization [ODBC]
ms.assetid: a2fa727e-51f2-4123-ae25-0ee28e611231
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a241ea92af6c1273039cc45daab232a1fbe763a3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081841"
---
# <a name="standard-programming-interface"></a>Standardprogrammierschnittstelle
Die Programmierschnittstelle ist vielleicht die am häufigsten offensichtlicher Kandidat für die Standardisierung. In der Tat, wenn ODBC entwickelt wird, ANSI und ISO bereits bereitgestellt Standards für embedded SQL und SQL Module. Obwohl keine Standards für eine Datenbank-CLI vorhanden war, wurde die Zugriffsgruppe für den SQL - ein Branchenkonsortium von Datenbankanbieter - angibt, ob eine erstellt in Betracht ziehen; ODBC-Komponenten, die höher ist die Grundlage für ihre Arbeit.  
  
 Eine der Anforderungen für ODBC war, dass eine einzelne Binärdateien der Anwendung mit mehreren DBMS zu arbeiten. Es ist deshalb, dass ODBC embedded SQL oder Modul Sprachen nicht verwendet wird. Obwohl die Sprache in eingebetteten SQL-Modul und den Sprachen standardisiert ist, ist jeweils mit DBMS-spezifische Precompilers verknüpft. Daher Anwendungen müssen neu kompiliert werden, für jede DBMS und die resultierenden Binärdateien funktionieren nur mit einer einzelnen DBMS. Obwohl dies für Anwendungen mit geringem Datenvolumen finden Sie in den Bereichen Minicomputer und Mainframe akzeptabel ist, ist es in der Welt der PC nicht zulässig. Erstens handelt es sich um eine logistische Alptraum mehrere Versionen der Software für Massenanfragen und eingeschweißte für Kunden bereitstellen; Zweitens müssen PC-Anwendungen häufig mehrere DBMS gleichzeitig zugreifen.  
  
 Auf der anderen Seite kann eine Call-Level-Interface implementiert werden, über die Bibliotheken oder Datenbanktreiber, die sich auf jedem lokalen Computer befinden; ein anderer Treiber ist für die jeweiligen Datenbankverwaltungssystem erforderlich. Da moderne Betriebssysteme diese Bibliotheken (z. B. Dynamic Link Libraries unter dem Betriebssystem Microsoft® Windows®) zur Laufzeit laden können, wird eine Anwendung auf Daten zugreifen kann aus verschiedenen DBMS-Systeme ohne Neukompilierung und kann auch auf Daten zugreifen. mehrere Datenbanken gleichzeitig. Sobald neue Datenbanktreiber verfügbar sind, können Benutzer nur installieren diese auf ihren Computern ohne ändern, neu kompilieren und verknüpfen Sie ihre datenbankanwendungen erneut. Darüber hinaus eine Call-Level-Interface war ein guter Kandidat für ODBC, da Windows - die Plattform für die ODBC ursprünglich entwickelt wurde-umfassenden Gebrauch von solchen Bibliotheken bereits vorgenommen.
