---
title: Eingebettete R Analytics-Lernprogramm für SQL Server-Machine Learning-Entwickler | Microsoft Docs
description: Lernprogramm zur Einbettung von R in SQL Server gespeicherte Prozeduren und Funktionen des T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d2b77d73bb1b8f5d4c507b884d0a09f4647012b
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250023"
---
# <a name="tutorial-embedded-r-in-stored-procedures-and-t-sql-functions"></a>Lernprogramm: Eingebetteten R in gespeicherten Prozeduren und T-SQL-Funktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Das Ziel dieses Lernprogramms ist SQL-Programmierer praktische Beispiele zum Erstellen eines Machine learning-Lösung in SQL Server bereitstellen. In diesem Lernprogramm erfahren Sie, wie Sie R in einer Anwendung oder eine BI-Lösung zu integrieren, indem Sie das Einschließen von R-Code in gespeicherten Prozeduren.

> [!NOTE]
> 
> Die gleiche Projektmappe ist in Python verfügbar. SQL Server-2017 ist erforderlich. Finden Sie unter [In der Datenbank Analytics für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Übersicht

Das Erstellen einer Ende-zu-Ende-Lösung besteht in der Regel aus Abrufen und Bereinigen von Daten, Durchsuchen von Daten und Verarbeiten von Funktionen, Modelltraining und Optimieren und schließlich Bereitstellung des Modells in der Produktion. Entwickeln und Testen von den tatsächlichen Code, wird am besten mit einer dedizierten Umgebung ausgeführt. Für R, das kann bedeuten RStudio oder [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Nachdem die Lösung erstellt wurde, können Sie sie jedoch problemlos für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)] -gespeicherten Prozeduren in der vertrauten Umgebung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]bereitstellen.

In diesem Lernprogramm wird davon ausgegangen, dass Sie alle R-Code, die erforderlich sind, für die Projektmappe, und den Fokus auf das Erstellen und Bereitstellen der Lösung mithilfe von SQL Server angegeben wurden.

- [Lektion 1: Herunterladen von Beispieldaten und Skripts](../tutorials/sqldev-download-the-sample-data.md)

- [Lektion 2: Einrichten der Umgebung Lernprogrammen](../r/sqldev-import-data-to-sql-server-using-powershell.md)

- [Lektion 3: Durchsuchen und Visualisieren von Daten strukturieren und Verteilung von R-Funktionen in gespeicherten Prozeduren aufrufen](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Lektion 4: Erstellen von Data-Funktionen, die mithilfe von R in T-SQL-Funktionen](../tutorials/sqldev-create-data-features-using-t-sql.md)
  
- [Lektion 5: Trainieren Sie, und speichern Sie ein R-Modells mithilfe von Funktionen und gespeicherten Prozeduren](../r/sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Lektion 6: Wrap R-Code in einer gespeicherten Prozedur für operationalisierung](../tutorials/sqldev-operationalize-the-model.md). 
  Nachdem das Modell in der Datenbank gespeichert wurde, rufen Sie das Modell für die Vorhersage von [!INCLUDE[tsql](../../includes/tsql-md.md)] mit gespeicherten Prozeduren auf.

## <a name="scenario"></a>Szenario

Dieses Lernprogramm verwendet ein bekannten öffentlichen Dataset basierend auf Reisen in New York City Taxi. Um den Beispielcode schneller ausgeführt werden soll, erstellt es einen repräsentativen Querschnitt der 1 % der Daten. Sie müssen diese Daten verwenden, ein binäres klassifizierungsmodell erstellen, das vorhersagt, ob es sich bei einem bestimmten Vorgang wahrscheinlich einen Tipp oder nicht abrufen wird basierend auf Spalten, z. B. den Zeitpunkt der Tag, Abstand und Abholung Speicherort.

## <a name="requirements"></a>Anforderungen

In diesem Lernprogramm wird davon ausgegangen mit grundlegenden Datenbankvorgängen wie Datenbanken und Tabellen erstellen, Importieren von Daten und das Schreiben von SQL-Abfragen vertraut sind. Es wird nicht davon ausgegangen, dass Sie wissen, dass R. Daher wird alle R-Code bereitgestellt. Ein erfahrener SQL-Programmierer können ein angegebenen PowerShell-Skripts Beispieldaten für GitHub erstellt und [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] um dieses Beispiel zu vervollständigen. 

Bevor Sie das Tutorial starten:

- Überprüfen, ob eine konfigurierte Instanz der [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) oder [SQL Server 2017 Machine Learning Services mit R aktiviert](../install/sql-machine-learning-services-windows-install.md#verify-installation). Darüber hinaus [bestätigen, dass Sie R-Bibliotheken](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).
- Der Anmeldename, mit denen Sie für dieses Lernprogramm benötigen Berechtigungen zum Erstellen von Datenbanken und anderen Objekten, zum Hochladen von Daten, wählen Sie die Daten, und führen Sie gespeicherte Prozeduren.

> [!NOTE]
> Es wird empfohlen, Sie führen **nicht** verwenden [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] schreiben oder R-Code zu testen. Wenn der Code, den Sie in einer gespeicherten Prozedur einbetten Probleme aufweist, sind die Informationen, die von der gespeicherten Prozedur zurückgegeben wird in der Regel unzureichend ist, um die Ursache des Fehlers zu verstehen.
> 
> Für das Debuggen, wird empfohlen, ein Tool wie z. B. [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], oder RStudio. Die in diesem Tutorial bereitgestellten R-Skripts wurden bereits mit herkömmlichen R-Tools entwickelt und debuggt.

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 1: Herunterladen der Beispieldaten](../tutorials/sqldev-download-the-sample-data.md)
