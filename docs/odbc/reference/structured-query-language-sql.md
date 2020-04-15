---
title: Strukturierte Abfragesprache (SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC]
- SQL [ODBC], about SQL
- ODBC [ODBC], SQL
ms.assetid: bebfd93e-0dc0-46b3-a531-518beb7ea976
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c669b4424271fc1a3c91dea37159474fb52b97cd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293390"
---
# <a name="structured-query-language-sql"></a>Structured Query Language (SQL) (Structured Query Language, SQL)
Ein typisches DBMS ermöglicht Benutzern das Speichern, Zugreifen und Ändern von Daten auf organisierte und effiziente Weise. Ursprünglich waren die Benutzer von DBMS Programmierer. Für den Zugriff auf die gespeicherten Daten musste ein Programm in einer Programmiersprache wie COBOL geschrieben werden. Während diese Programme oft geschrieben wurden, um eine benutzerfreundliche Schnittstelle für einen nichttechnischen Benutzer zu präsentieren, erforderte der Zugriff auf die Daten selbst die Dienste eines sachkundigen Programmierers. Der gelegentliche Zugriff auf die Daten war nicht praktikabel.  
  
 Die Nutzer waren mit dieser Situation nicht ganz zufrieden. Obwohl sie auf Daten zugreifen konnten, musste oft ein DBMS-Programmierer davon überzeugt werden, spezielle Software zu schreiben. Wenn z. B. eine Vertriebsabteilung den Gesamtumsatz des Vormonats von jedem ihrer Vertriebsmitarbeiter anzeigen wollte und diese Informationen nach der Dienstdauer jedes Verkäufers im Unternehmen ordnen wollte, hatte sie zwei Möglichkeiten: Entweder gab es bereits ein Programm, das den Zugriff auf die Informationen genau auf diese Weise ermöglichte, oder die Abteilung musste einen Programmierer bitten, ein solches Programm zu schreiben. In vielen Fällen war dies mehr Arbeit, als es wert war, und es war immer eine teure Lösung für einmalige oder ad hoc Anfragen. Da immer mehr Benutzer einen einfachen Zugriff wünschten, wurde dieses Problem immer größer.  
  
 Um den Benutzern den Ad-hoc-Zugriff auf Daten zu ermöglichen, war es erforderlich, ihnen eine Sprache zu geben, in der sie ihre Anträge äußern können. Eine einzelne Anforderung an eine Datenbank wird als Abfrage definiert. eine solche Sprache wird als Abfragesprache bezeichnet. Viele Abfragesprachen wurden zu diesem Zweck entwickelt, aber eine davon wurde die beliebteste: Structured Query Language, erfunden bei IBM in den 1970er Jahren. Es ist allgemein bekannt unter seinem Akronym, SQL, und wird sowohl als "ess-cue-ell" als auch als "Sequel" ausgesprochen. SQL wurde 1986 zum ANSI-Standard und 1987 zum ISO-Standard. es wird heute in vielen Datenbankverwaltungssystemen verwendet.  
  
 Obwohl SQL die Ad-hoc-Anforderungen der Benutzer löste, ging die Notwendigkeit für den Datenzugriff durch Computerprogramme nicht weg. Tatsächlich war (und ist) der größte Teil des Datenbankzugriffs immer noch programmatisch, in Form von regelmäßig geplanten Berichten und statistischen Analysen, Dateneingabeprogrammen, wie sie für die Auftragserfassung verwendet werden, und Datenmanipulationsprogrammen, wie sie zum Abgleichen von Konten und generieren von Arbeitsaufträgen verwendet werden.  
  
 Diese Programme verwenden auch SQL, mit einer der folgenden drei Techniken:  
  
-   **Embedded SQL**, in dem SQL-Anweisungen in eine Hostsprache wie C oder COBOL eingebettet sind.  
  
-   **SQL-Module**, in denen SQL-Anweisungen auf dem DBMS kompiliert und von einer Hostsprache aufgerufen werden.  
  
-   Schnittstelle auf **Aufrufebene**, oder CLI, die aus Funktionen besteht, die aufgerufen werden, SQL-Anweisungen an das DBMS zu übergeben und Ergebnisse aus dem DBMS abzurufen.  
  
> [!NOTE]  
>  Es ist ein historischer Unfall, dass der Begriff Schnittstelle auf Aufrufebene anstelle der API (Application Programming Interface) verwendet wird, ein anderer Begriff für dasselbe. In der Datenbankwelt wird API verwendet, um SQL selbst zu beschreiben: SQL ist die API für ein DBMS.  
  
 Von diesen Optionen ist Embedded SQL die am häufigsten verwendete, obwohl die meisten großen DBMS proprietäre CLIs unterstützen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verarbeiten einer SQL-Anweisung](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [Embedded SQL](../../odbc/reference/embedded-sql.md)  
  
-   [SQL-Module](../../odbc/reference/sql-modules.md)  
  
-   [Call-Level-Interface](../../odbc/reference/call-level-interfaces.md)
