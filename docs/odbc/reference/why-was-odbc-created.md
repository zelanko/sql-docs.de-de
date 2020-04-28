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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302781"
---
# <a name="why-was-odbc-created"></a>Warum wurde ODBC erstellt?
In der Vergangenheit haben Unternehmen ein einzelnes DBMS verwendet. Der gesamte Datenbankzugriff erfolgte entweder über das Front-End des Systems oder über Anwendungen, die für das ausschließliche arbeiten mit diesem System geschrieben wurden. Da jedoch die Verwendung von Computern und mehr Computer Hardware und Software zur Verfügung gestellt wurde, begannen Unternehmen, andere DBMSs zu erwerben. Die Gründe hierfür sind: Personen haben gekauft, was am billigsten war, was am schnellsten war, was Sie bereits wussten, was das neueste auf dem Markt war, was am besten für eine einzelne Anwendung funktionierte. Andere Gründe hierfür sind Neuorganisationen und Fusionen, bei denen Abteilungen, die zuvor ein einzelnes DBMS besaßen, jetzt mehrere haben.  
  
 Das Problem ist mit der Einführung von PCs noch komplexer geworden. Diese Computer haben eine Reihe von Tools zum Abfragen, analysieren und Anzeigen von Daten zusammen mit einer Reihe von kostengünstigen, leicht zu verwendenden Datenbanken integriert. Von einem anderen Unternehmen verfügten die Daten häufig über eine Vielzahl von Desktops, Servern und Mini Computern, die in einer Vielzahl von nicht kompatiblen Datenbanken gespeichert wurden, und auf die durch eine Vielzahl verschiedener Tools zugegriffen werden konnte, von denen nur wenige die Daten erhalten konnten.  
  
 Die letzte Herausforderung kam bei der Einführung von Client-/Server-Computing, bei dem die Verwendung von Computerressourcen möglichst effizient ist. Kostengünstige PCs (Clients) befinden sich auf dem Desktop und bieten sowohl ein grafisches Front-End für die Daten als auch eine Reihe von kostengünstigen Tools, wie z. b. Kalkulations Tabellen, Diagramm-Programme und Berichts-Generatoren. Minicomputers und Main Frame Computer (die Server) hosten die DBMSs, wo Sie Ihre computeleistung und den zentralen Standort verwenden können, um schnellen, koordinierten Datenzugriff bereitzustellen. Wie sollte die Front-End-Software dann mit den Back-End-Datenbanken verbunden werden?  
  
 Ein ähnliches Problem bei unabhängigen Softwareanbietern (ISVs). Anbieter, die Datenbanksoftware für Minicomputer und Mainframes schreiben, mussten in der Regel eine Version einer Anwendung für jedes DBMS schreiben oder DBMS-spezifischen Code für jedes DBMS schreiben, auf das Sie zugreifen wollten. Hersteller, die Software für PCs schreiben, mussten Datenzugriffs Routinen für jedes andere DBMS schreiben, mit dem Sie arbeiten wollten. Dies bedeutete häufig, dass eine große Menge an Ressourcen für das Schreiben und Verwalten von Datenzugriffs Routinen anstelle von Anwendungen aufgewendet wurde, und Anwendungen waren oft nicht in ihrer Qualität verkauft, sondern darauf, ob Sie auf Daten in einem bestimmten DBMS zugreifen konnten.  
  
 Was beide Entwickler Gruppen benötigten, war eine Möglichkeit für den Zugriff auf Daten in unterschiedlichen DBMSs. Die Gruppe "Main Frame" und "Minicomputer" benötigte eine Möglichkeit zum Zusammenführen von Daten aus unterschiedlichen DBMSs in einer einzelnen Anwendung, während die persönliche Computergruppe diese Möglichkeit benötigte, und eine Möglichkeit zum Schreiben einer einzelnen Anwendung, die unabhängig von einem DBMS war. Kurz gesagt, beide Gruppen benötigten eine interoperable Möglichkeit, um auf Daten zuzugreifen. Sie benötigten eine offene Datenbankverbindung.
