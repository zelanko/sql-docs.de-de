---
title: Structured Query Language (SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC]
- SQL [ODBC], about SQL
- ODBC [ODBC], SQL
ms.assetid: bebfd93e-0dc0-46b3-a531-518beb7ea976
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a32983b1dd4faaa64c09f5ccc773fd4ce78f3533
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909550"
---
# <a name="structured-query-language-sql"></a>Structured Query Language (SQL) (Structured Query Language, SQL)
Ein typisches DBMS ermöglicht das Speichern, Zugriff auf und Ändern von Daten in eine strukturierte und effiziente Weise. Ursprünglich waren die Benutzer des DBMS Programmierer. Zugreifen auf die gespeicherten Daten erforderlich, das Schreiben eines Programms in einer Programmiersprache wie z. B. COBOL. Aber dieser Programme häufig geschrieben wurden, eine benutzerfreundliche Schnittstelle, die nicht technischen Benutzer angezeigt, erforderlich, den Zugriff auf die Daten selbst die Dienste der Programmierer informiert. Einer zufälligen Zugriff auf die Daten wurde nicht praktikabel.  
  
 Benutzer konnten nicht ganz glücklich mit dieser Situation. Während sie auf Daten zugreifen können, musste jedoch häufig ein überzeugender DBMS Programmierer sind speziellen Software zu schreiben. Z. B. wenn eine Verkaufsabteilung möchte den Gesamtumsatz im vorherigen Monat von jedem der Vertriebsmitarbeiter, finden Sie unter und diese Informationen, die Rangfolge nacheinander jedes Vertriebsmitarbeiters Länge des Diensts in das Unternehmen wollte, musste es zwei Möglichkeiten: entweder ein Programm war bereits vorhanden, die die Informationen auf genau diese Weise zugegriffen werden darf, oder die Abteilung stellen einen Programmierer, die ein solches Programm schreiben mussten. In vielen Fällen war das mehr Arbeit als ich sollte, und es handelte sich immer um eine teure Lösung für einmalige oder ad-hoc-, Anfragen. Da immer mehr Benutzer einfach zugreifen möchten, wächst dieses Problem, größere.  
  
 Ermöglicht Benutzern den Zugriff auf Daten auf einer ad-hoc-Basis erforderlich, sodass sie eine Sprache, die zum Ausdrücken von ihren Anforderungen. Eine einzelne Anforderung in einer Datenbank wird als eine Abfrage definiert. einer solchen Sprache wird eine Abfragesprache aufgerufen. Viele Abfragesprachen für diesen Zweck entwickelt wurden, aber eine davon ist die am häufigsten verwendeten: Structured Query Language, bei IBM in den 1970er Jahren erfunden. Es wird häufig durch die SQL-Akronym bezeichnet und ist besonders ausgeprägt, sowohl als "Ess-Cue-Ell" als "Fortsetzung". SQL wurde eine ANSI-standard im Jahr 1986 und ein ISO-standard, 1987; Es ist heute in eine hervorragende viele Managementsysteme für Datenbanken verwendet.  
  
 Obwohl SQL die ad-hoc-Anforderungen von Benutzern gelöst werden, müssen für den Datenzugriff von Computerprogrammen nicht verschwinden. In der Tat die meisten Zugriff auf die Datenbank weiterhin (und) programmgesteuerten, in Form von regelmäßigen Berichten und statistische Analysen, die Dateneingabe Programme, z. B. die Manipulation-Programme, z. B. zum Abstimmen für Auftragseingabe und Daten verwendet und Arbeitsaufträge zu generieren.  
  
 Diese Programme verwenden auch SQL-Anweisung mit einer der folgenden drei Methoden:  
  
-   **Embedded SQL**, in dem SQL-Anweisungen in eine Hostsprache, wie z. B. C oder COBOL eingebettet sind.  
  
-   **SQL-Module**, welche SQL-Anweisungen für das DBMS kompiliert und von einer Hostsprache aufgerufen werden.  
  
-   **Call-Level-Interface**, oder die CLI, Funktionen, die aufgerufen wird, um SQL-Anweisungen für das DBMS zu übergeben und zum Abrufen der Ergebnisse aus dem DBMS besteht.  
  
> [!NOTE]  
>  Es handelt sich um eine historische versehentlich, die den Begriff Call-Level-Interface verwendet, anstatt die anwendungsprogrammierung (API),-Schnittstelle eine andere Bezeichnung für das gleiche. In der Datenbankwelt-API wird verwendet, um die SQL selbst zu beschreiben: SQL ist die API für ein DBMS.  
  
 Diese Optionen ist ein embedded SQL die am häufigsten verwendeten, obwohl die meisten wichtige Datenbankmanagementsysteme proprietäre CLIs unterstützen.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Verarbeiten einer SQL­Anweisung](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [Embedded SQL](../../odbc/reference/embedded-sql.md)  
  
-   [SQL-Module](../../odbc/reference/sql-modules.md)  
  
-   [Call-Level-Interface](../../odbc/reference/call-level-interfaces.md)
