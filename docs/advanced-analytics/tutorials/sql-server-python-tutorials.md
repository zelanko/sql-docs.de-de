---
title: SQL Server Python-Tutorials | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 541675c22ddbe347f67119d8cba82f75955382e6
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48877984"
---
# <a name="sql-server-python-tutorials"></a>SQL Server Python-tutorials
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält eine Liste der Tutorials und Beispiele, in denen die Verwendung von Python mit SQL Server 2017. Durch diese Beispiele und Demos lernen Sie Folgendes:

+ Gewusst wie: Ausführen von Python und T-SQL
+ Was sind die lokalen und remote computekontexte und wie Sie Python-Code mithilfe von SQL Server-Computers ausführen können
+ Gewusst wie: Umschließen von Python-Code in einer gespeicherten Prozedur
+ Optimieren von Python-Code für eine SQL-produktionsumgebung
+ Reale Szenarien für die Einbettung von Machine Learning in Anwendungen

Weitere Informationen zu Anforderungen und Setup, finden Sie unter [Voraussetzungen](#bkmk_Prerequisites).

## <a name="bkmk_pythontutorials"></a>Python-tutorials

+ [Ausführung von Python in T-SQL](run-python-using-t-sql.md)

   Enthält die Grundlagen zum Aufrufen von Python in T-SQL mit den Erweiterungsmechanismus, der in SQL Server 2016 eine Vorreiterrolle einnimmt.

+ [Erstellen eines Machine learning-Modell in Python mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md)

   In dieser Lektion wird veranschaulicht, wie Sie Code von einem remote-Python-Terminal ausführen können mithilfe von SQL Server-computekontext. Sie sollten etwas mit Python-Tools und Umgebungen vertraut sein. Ist Beispielcode bereitgestellt, die ein Modell mithilfe erstellt **RxLinMod**, aus dem neuen **Revoscalepy** Bibliothek. 

+ [In-Database Python Analytics für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md)

    Diese exemplarische End-to-End-Vorgehensweise wird veranschaulicht, wie zum Erstellen einer vollständigen Python-Lösung mithilfe von gespeicherten T-SQL-Prozeduren. Alle Python-Code ist enthalten.


## <a name="python-samples"></a>Python-Beispiele

Markieren Sie diese Beispiele und Demos, die von der SQL Server-Entwicklungsteam bereitgestellte Methoden, mit denen Sie eingebettete Analysen in realen Anwendungen verwenden können.

+ [Erstellen eines Vorhersagemodells mithilfe von Python und SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Erfahren Sie, wie ein skiverleih Machine learning, um zukünftige verleihe vorherzusagen, wodurch die Business-Plan und die Mitarbeiter, von der zukünftigen Nachfrage zu begegnen verwenden kann.

  > [!TIP]
  > Enthält jetzt die nativen Bewertung von Python-Modelle.

+ [Ausführen von Kunden mithilfe von Python und SQL Server-clustering](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Erfahren Sie, wie Sie mit der k-Means-Algorithmus zum Ausführen von nicht überwachten Gruppieren von Kunden.

## <a name="bkmk_Prerequisites"></a>Voraussetzungen

Um diese Lernprogramme verwenden zu können, benötigen Sie SQL Server 2017, und Sie müssen explizit installieren und aktivieren dann das Feature, Machine Learning Services (Datenbankintern). 

SQL Server 2017 unterstützt die R und Python-Sprachen, aber keines von beiden installiert oder in der Standardeinstellung aktiviert wird. Ausführung von Python ist erforderlich, dass es sich bei das Extensibility Framework aktiviert werden und Sie Python als Sprache für die Installation auswählen. 

### <a name="post-installation-configuration-tips"></a>Tipps zum nach der Installation konfigurieren

Nach dem SQL Server-Setup ausführen, müssen Sie möglicherweise einige zusätzliche Schritte, um sicherzustellen, dass Python- und SQL Server kommunizieren ausführen:

+ Die Features zur externen skriptausführung aktivieren, indem Sie Ausführung `sp_configure 'external scripts enabled', 1`.
+ Starten Sie den Server neu. 
+ Öffnen der **Services** Bereich zu überprüfen, ob Launchpad gestartet wurde. 
+ Stellen Sie sicher, dass der Dienst, der die externe Runtime Ruft die erforderlichen Berechtigungen verfügt. Weitere Informationen finden Sie unter [Aktivieren der impliziten Authentifizierung](../security/add-sqlrusergroup-to-database.md).
+ Öffnen eines Ports in der Firewall für SQL Server, und aktivieren Sie die erforderlichen Netzwerkprotokollen.
+ Stellen Sie sicher, dass Ihr SQL-Anmeldung oder der Windows-Benutzerkonto die erforderlichen Berechtigungen zum Verbinden mit dem Server, der zum Lesen von Daten und erstellen das Beispiel erforderlichen Datenbankobjekte verfügt.

Finden Sie in diesem Artikel einige häufig auftretende Probleme: [Problembehandlung bei Machine Learning Services](../machine-learning-troubleshooting-faq.md)

### <a name="resource-management"></a>Ressourcenverwaltung

Sie können R und Python auf dem gleichen Computer installieren, aber ausführt, kann erhebliche Ressourcen erfordern. Wenn "nicht genügend Arbeitsspeicher" Fehler auftreten oder Machine Learning-Aufträge ausführen, dass der Prinzipal mit dem Server vorgesehen ist, können Sie die Größe des Arbeitsspeichers reduzieren, die die Datenbank-Engine zugeordnet ist. Weitere Informationen finden Sie unter [verwalten und Überwachen von Python in SQL Server](../python/managing-and-monitoring-python-solutions.md).

## <a name="see-also"></a>Siehe auch

[R-Tutorials für SQL Server](sql-server-r-tutorials.md)
