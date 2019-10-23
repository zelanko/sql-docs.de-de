---
title: Überwachen der Python-und R-Skriptausführung mithilfe von benutzerdefinierten Berichten in SSMS
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 549cdcd35b939b2247b14817271e3d1063fab1e0
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714394"
---
# <a name="monitor-python-and-r-script-execution-using-custom-reports-in-sql-server-management-studio"></a>Überwachen der Python-und R-Skriptausführung mit benutzerdefinierten Berichten in SQL Server Management Studio
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Verwenden Sie benutzerdefinierte Berichte in SQL Server Management Studio (SSMS), um die Ausführung externer Skripts (python und R), die verwendeten Ressourcen, die Diagnose von Problemen und die Leistungsoptimierung in SQL Server Machine Learning Services zu überwachen.

In diesen Berichten können Sie Details wie die folgenden anzeigen:

- Aktive python-oder R-Sitzungen
- Konfigurationseinstellungen für die Instanz
- Ausführungs Statistik für Machine Learning-Aufträge
- Erweiterte Ereignisse für R Services
- Auf der aktuellen Instanz installierte python-oder R-Pakete

In diesem Artikel wird erläutert, wie Sie die für SQL Server Machine Learning Services bereitgestellten benutzerdefinierten Berichte installieren und verwenden.

Weitere Informationen zu Berichten in SQL Server Management Studio finden Sie unter [benutzerdefinierte Berichte in Management Studio](../../ssms/object/custom-reports-in-management-studio.md).

## <a name="how-to-install-the-reports"></a>So führen Sie die Installation von Berichten durch

Die Berichte werden mit SQL Server Reporting Services entworfen, können jedoch direkt von SQL Server Management Studio verwendet werden. Reporting Services muss nicht auf Ihrer SQL Server-Instanz installiert werden.

Um diese Berichte zu verwenden, führen Sie die folgenden Schritte aus:

1. Laden Sie die [benutzerdefinierten SSMS-Berichte](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports) für SQL Server Machine Learning Services von GitHub herunter.

2. Kopieren der Berichte in Management Studio

    1. Suchen Sie den Ordner der benutzerdefinierten Berichte, der von SQL Server Management Studio verwendet wird. Standardmäßig werden benutzerdefinierte Berichte in diesem Ordner gespeichert (wobei **user_name** für den Windows-Benutzernamen steht):

        `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

       Sie können auch einen anderen Ordner angeben oder Unterordner erstellen.

    2. Kopieren Sie die *. RDL-Dateien, die Sie in den Ordner benutzerdefinierte Berichte heruntergeladen haben

3. Führen Sie die Berichte in Management Studio

    1. Klicken Sie in Management Studio mit der rechten Maustaste auf den Knoten **Datenbanken** der Instanz, auf der Sie die Berichte ausführen möchten.

    2. Klicken Sie auf **Berichte**, und klicken Sie dann auf **Benutzerdefinierte Berichte**.

    3. Suchen Sie im Dialogfeld **Datei öffnen** den Ordner mit den benutzerdefinierten Berichten.

    4. Wählen Sie eine der RDL-Dateien aus, die Sie heruntergeladen haben, und klicken Sie dann auf **Öffnen**.

## <a name="reports"></a>Berichte

Das [SSMS-Repository für benutzerdefinierte Berichte in GitHub](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports) enthält die folgenden Berichte:

| Bericht | Beschreibung |
|-|-|
| Aktive Sitzungen | Benutzer, die derzeit mit der SQL Server Instanz verbunden sind und ein Python-oder R-Skript ausführen. |
| Konfiguration | Installationseinstellungen für Machine Learning Services und Eigenschaften der Python-oder R-Laufzeit. |
| Instanz konfigurieren | Konfigurieren Sie Machine Learning Services. |
| Ausführungs Statistik | Ausführungs Statistik der Machine Learning Dienste. Beispielsweise können Sie die Gesamtzahl der Ausführungen externer Skripts und die Anzahl paralleler Ausführungen erhalten. |
| Erweiterte Ereignisse | Erweiterte Ereignisse, die verfügbar sind, um mehr Einblicke in die Ausführung externer Skripts zu erhalten. |
| Pakete | Auflisten der auf der SQL Server Instanz installierten R-oder python-Pakete und ihrer Eigenschaften, z. b. Version und Name. |
| Resource Usage | Anzeigen der CPU, des Arbeitsspeichers, der e/a-Nutzung von SQL Server und der Ausführung externer Skripts. Sie können auch die Arbeitsspeicher Einstellung für externe Ressourcenpools anzeigen. |

## <a name="next-steps"></a>Nächste Schritte

- [Überwachen von SQL Server Machine Learning Services mithilfe dynamischer Verwaltungs Sichten (DMVs)](monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)
- [Extended events for R Services (Erweiterte Ereignisse bei R Services)](../r/extended-events-for-sql-server-r-services.md)
