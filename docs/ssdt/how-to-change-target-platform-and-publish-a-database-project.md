---
title: Ändern der Zielplattform und Veröffentlichen eines Datenbankprojekts
description: In diesem Artikel erfahren Sie, wie Sie die Plattform für ein Datenbankprojekt in SQL Server Data Tools in eine unterstützte SQL Server-Instanz ändern. Außerdem erfahren Sie, wie Sie ein Datenbankprojekt veröffentlichen.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.publish.dialog
- sql.data.tools.publishdacproject
ms.assetid: 6012e120-5f72-4f4f-ae6e-f9a57ae1dea7
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: c5ee0b9febeec7da287e26a40adcb6910b80991d
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987216"
---
# <a name="how-to-change-target-platform-and-publish-a-database-project"></a>Gewusst wie: Ändern der Zielplattform und Veröffentlichen eines Datenbankprojekts

Sie können die SQL Server-Zielversion für Ihr SSDT-Datenbankprojekt (SQL Server Data Tools) in jede unterstützte SQL Server-Instanz (SQL Server 2005, 2008, 2008 R2, Microsoft SQL Server 2012 oder SQL Azure) ändern. Hierdurch können Sie die Datenbankentwicklung in einem einzelnen Projekt bündeln, das Projekt jedoch bei Bedarf in mehreren SQL Server-Instanzen veröffentlichen.  
  
SSDT vereinfacht auch diese Aufgabe durch Berücksichtigung der Zielplattform und automatisches Erkennen sämtlicher Fehler im Code (z. B. bei Verwendung von nicht unterstützten Funktionen für ein Projekt, das in SQL Azure veröffentlicht werden soll).  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-change-a-projects-target-platform"></a>So ändern Sie die Zielplattform eines Projekts  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus. Klicken Sie links auf die Registerkarte **Projekteinstellungen** , um die Eigenschaftenseite **Projekteinstellungen** zu öffnen.  
  
2.  Die Dropdownliste **Zielplattform** auf dieser Seite enthält alle unterstützten SQL Server-Plattformen, auf denen ein Datenbankprojekt veröffentlicht werden kann. Wählen Sie für diese Prozedur **SQL Azure**aus.  
  
### <a name="to-use-platform-validation-when-editing-scripts"></a>So verwenden Sie beim Bearbeiten von Skripts Plattformüberprüfung  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Tabelle **Products**, und wählen Sie **Code anzeigen** aus, um die Tabelle im Transact\-SQL-Editor zu öffnen.  
  
2.  Fügen Sie an das Ende der `ON [PRIMARY]` -Anweisung `CREATE TABLE` an.  
  
3.  Beachten Sie, dass im Bereich **Fehlerliste** der folgende Fehler angezeigt wird: „SQL70015: "Dateigruppenverweis und Partitionierungsschema" wird in SQL Azure nicht unterstützt.“  
  
    SSDT überprüft das Skript automatisch auf Grundlage der Zielplattform. Da Dateigruppen in SQL Azure nicht unterstützt werden, gibt SSDT in diesem Fall einen Fehler zurück. Eine Liste der in SQL Azure nicht unterstützten Transact\-SQL-Anweisungen finden Sie unter [Teilweise unterstützte Transact-SQL-Anweisungen (Microsoft Azure SQL-Datenbank)](/previous-versions/azure/ee336267(v=azure.100)).  
  
4.  Entfernen Sie die `ON` -Klausel. Beachten Sie, dass der Fehler unmittelbar darauf nicht mehr in der **Fehlerliste**angezeigt wird.  
  
### <a name="to-publish-a-database-project"></a>So veröffentlichen Sie ein Datenbankprojekt  
  
1.  Wenn Sie Zugriff auf eine SQL Azure-Instanz haben, können Sie mit dem nächsten Schritt fortfahren. Klicken Sie andernfalls im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TradeDev**, und klicken Sie auf **Eigenschaften**, um auf die Eigenschaftenseite **Projekteinstellungen** zuzugreifen. Verwenden Sie die Dropdownliste **Zielplattform**, um die SQL Server-Plattform auszuwählen, auf der Sie das Projekt veröffentlichen möchten.  
  
2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TradeDev**, und wählen Sie **Veröffentlichen** aus. SSDT beginnt mit dem Erstellen des Projekts. Wenn kein Buildfehler auftritt, wird das Dialogfeld **Datenbank veröffentlichen** angezeigt.  
  
3.  Klicken Sie im Dialogfeld **Datenbank veröffentlichen** auf **Bearbeiten** , um die Zieldatenbankverbindung zu bearbeiten.  
  
4.  Geben Sie im Dialogfeld **Verbindungseigenschaften** zur Authentifizierung den Namen der SQL Server-Instanz und Ihre Anmeldeinformationen ein. Geben Sie in **Mit Datenbank verbinden**den Wert **NewTrade**ein. Hierdurch wird versucht, das Datenbankprojekt in einer neuen Datenbank zu veröffentlichen. Sie können zum Veröffentlichen des Projekts auch eine vorhandene Datenbank auswählen. Wenn Sie z.B. die vorhandene Datenbank **TradeDev** auswählen, werden alle Änderungen, die Sie im Offlineprojekt **TradeDev** an den Objekten (als Skripts) vorgenommen haben, an die Livedatenbank **TradeDev** weitergegeben.  
  
    Wenn Sie über die Berechtigung verfügen, Änderungen an der Datenbank vorzunehmen, in der Sie das Projekt veröffentlichen möchten, klicken Sie auf die Schaltfläche **Veröffentlichen** . Wenn Sie jedoch keinen Schreibzugriff auf eine Produktionsdatenbank haben, können Sie auf die Schaltfläche **Skript generieren** klicken, um ein Transact\-SQL-Veröffentlichungsskript zu erzeugen, das anschließend an einen Datenbankadministrator übergeben werden kann. Der Datenbankadministrator kann dann das Skript ausführen, um den Produktionsserver zu aktualisieren, damit dessen Schema mit dem Datenbankprojekt synchron ist.  
  
5.  Im Fenster **Datentoolvorgänge**  werden der Status der Veröffentlichungsvorgänge und ggf. Fehlermeldungen angezeigt. In diesem neuen Fenster können Sie ggf. auch die Vorschau der Bereitstellung, das generierte Skript oder sämtliche Veröffentlichungsergebnisse anzeigen.  
  
6.  Sie können auch die Veröffentlichungseinstellungen in einem Profil speichern, damit Sie für zukünftige Veröffentlichungsvorgänge die gleichen Einstellungen wiederverwenden können. Klicken Sie hierzu im Dialogfeld **Datenbank veröffentlichen** auf die Schaltfläche **Profil speichern unter** . Wenn Sie vorhandene Einstellungen in der Zukunft erneut laden möchten, können Sie auf die Schaltfläche **Profil laden** klicken.  
  
7.  Beachten Sie die Meldungen im Fenster **Datentoolvorgänge** . Klicken Sie rechts von **Veröffentlichungsvorschau wird erstellt...** auf „Vorschau anzeigen“. auf den Link "Vorschau anzeigen". Dadurch wird der Bereitstellungsvorschaubericht geöffnet. Wenn die Zielplattform des Projekts nicht mit dem Datenbankserver identisch ist, auf dem das Projekt veröffentlicht wird, gibt SSDT in diesem Bericht eine Warnung aus.  Wenn z. B. die Zielplattform des Projekts Microsoft SQL Server 2012 ist und Sie versuchen, das Projekt in einer SQL Server 2008 R2-Serverinstanz zu veröffentlichen, wird im **Ausgabefenster** die folgende Warnung angezeigt:  
  
**Bei einem Projekt, bei dem Microsoft SQL Server 2012 als Zielplattform angegeben ist, können möglicherweise Kompatibilitätsprobleme mit SQL Server 2008 auftreten.** Enthält ein solches Projekt Entitäten (z.B. ein Sequenzobjekt), die in Microsoft SQL Server 2012 eingeführt wurden, tritt beim Veröffentlichungsvorgang ein Fehler auf.  
  
Bei der Bereitstellung tritt ein Fehler auf, wenn Objektprädikate **CONTAINS** oder **FREETEXT** für einen neu erstellten Volltextindex verwenden und Transaktionsskripts eingesetzt werden. Wenn die Option zum Einschließen von Transaktionsskripts während der Bereitstellung aktiviert ist, werden Prozeduren und Sichten innerhalb einer Transaktion definiert, während ein Volltextindex außerhalb einer Transaktion am Ende des Bereitstellungsskripts definiert wird. Aufgrund dieser im Skript vorgegebenen Reihenfolge werden Prozeduren oder Sichten, die CONTAINS oder FREETEXT verwenden, nicht anhand des Volltextindexes aufgelöst, was zu einem Bereitstellungsfehler führt.  
