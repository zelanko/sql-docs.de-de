---
title: Warum wurde ODBC erstellt? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], about ODBC
ms.assetid: ba6eb993-316b-4650-bab8-d76583c00e53
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 22173b0ad3dd8abf2d168b41a16a03bc414022ce
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302781"
---
# <a name="why-was-odbc-created"></a>Warum wurde ODBC erstellt?
In der Vergangenheit verwendeten Unternehmen ein einzelnes DBMS. Der gesamte Datenbankzugriff erfolgte entweder über das Front-End dieses Systems oder über Anwendungen, die geschrieben wurden, um ausschließlich mit diesem System zu arbeiten. Als jedoch die Nutzung von Computern zunahm und immer mehr Computerhardware und -software verfügbar wurden, begannen Unternehmen, verschiedene DBMS zu erwerben. Die Gründe waren vielfältig: Die Leute kauften, was am billigsten war, was am schnellsten war, was sie bereits wussten, was das Neueste auf dem Markt war, was für eine einzige Anwendung am besten funktionierte. Weitere Gründe waren Umstrukturierungen und Fusionen, bei denen Abteilungen, die zuvor über ein einziges DBMS verfügten, nun mehrere hatten.  
  
 Das Problem wurde mit dem Aufkommen von PCs noch komplexer. Diese Computer brachten eine Vielzahl von Tools zum Abfragen, Analysieren und Anzeigen von Daten sowie eine Reihe kostengünstiger, benutzerfreundlicher Datenbanken ein. Von da an verfügte ein einzelnes Unternehmen häufig über Daten, die über eine Vielzahl von Desktops, Servern und Minicomputern verstreut waren, die in einer Vielzahl inkompatibler Datenbanken gespeichert waren und auf die von einer Vielzahl verschiedener Tools zugegriffen wurde, von denen nur wenige die Daten erhalten konnten.  
  
 Die letzte Herausforderung kam mit dem Aufkommen von Client/Server-Computing, das versucht, die effizientesten Nutzung von Computerressourcen zu machen. Günstige PCs (die Clients) befinden sich auf dem Desktop und bieten sowohl ein grafisches Front-End für die Daten als auch eine Reihe kostengünstiger Tools wie Tabellenkalkulationen, Diagrammprogramme und Berichtserbauern. Minicomputer und Mainframe-Computer (die Server) hosten die DBMS, wo sie ihre Rechenleistung und ihren zentralen Standort nutzen können, um einen schnellen, koordinierten Datenzugriff zu ermöglichen. Wie sollte dann die Front-End-Software mit den Back-End-Datenbanken verbunden werden?  
  
 Ein ähnliches Problem betraf unabhängige Softwareanbieter (ISVs). Anbieter, die Datenbanksoftware für Minicomputer und Mainframes schreiben, waren in der Regel gezwungen, für jedes DBMS eine Version einer Anwendung zu schreiben oder DBMS-spezifischen Code für jedes DBMS zu schreiben, auf das sie zugreifen wollten. Anbieter, die Software für PCs schreiben, mussten Datenzugriffsroutinen für jedes dbMS schreiben, mit dem sie arbeiten wollten. Dies bedeutete häufig, dass eine große Menge an Ressourcen für das Schreiben und Verwalten von Datenzugriffsroutinen und nicht für Anwendungen aufgewendet wurde, und Anwendungen wurden oft nicht nach ihrer Qualität verkauft, sondern danach, ob sie auf Daten in einem bestimmten DBMS zugreifen konnten.  
  
 Beide Entwicklergruppen benötigten eine Möglichkeit, auf Daten in verschiedenen DBMS zuzugreifen. Die Mainframe- und Minicomputergruppe benötigte eine Möglichkeit, Daten aus verschiedenen DBMS in einer einzigen Anwendung zusammenzuführen, während die PC-Gruppe diese Fähigkeit sowie eine Möglichkeit benötigte, eine einzelne Anwendung zu schreiben, die unabhängig von einem DBMS war. Kurz gesagt, beide Gruppen benötigten eine interoperable Möglichkeit, auf Daten zuzugreifen; Sie benötigten eine offene Datenbankkonnektivität.
