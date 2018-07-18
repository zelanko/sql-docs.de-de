---
title: R-Interoperabilität in SQL Server R Services|Microsoft-Dokumente
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: da739700cabb6a9d691d5f284cd6f0532898393f
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979022"
---
# <a name="r-interoperability-in-sql-server"></a>R-Interoperabilität in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieses Thema konzentriert sich auf den Mechanismus zum Ausführen von R in SQL Server und beschreibt die Unterschiede zwischen Microsoft R und open-Source-R.

Gilt für: SQL Server 2016 R Services, SqlServer 2017 Machine Learning-Dienste

Weitere Informationen zu zusätzlichen Komponenten finden Sie unter [neue Komponenten in SQL Server](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md).

### <a name="open-source-r-components"></a>Open-Source-R-Komponenten

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] enthält eine vollständige Verteilung der Basis-R-Pakete und -Tools. Weitere Informationen darüber, was in der Basis-Verteilung enthalten ist, finden Sie unter der Dokumentation, die während der Installation den folgenden standardmäßigen Speicherort installiert: `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

Im Rahmen der Installation von [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], müssen Sie den Bedingungen der öffentlichen GNU-Lizenz zustimmen. Anschließend können Sie Standard-R-Pakete ohne weitere Änderungen ausführen, wie in anderen Open-Source-Verteilungen von R.

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ändert die R-Laufzeit in keiner Weise. Die R-Laufzeit wird außerhalb des [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Prozesses ausgeführt und kann unabhängig von [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ausgeführt werden. Es wird jedoch dringend empfohlen, diese Tools nicht zu verwenden, während [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] R verwendet, um Ressourcenkonflikte zu vermeiden.

Die R-Basispaket-Verteilung, die mit einer bestimmten [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Instanz verknüpft ist, finden Sie in dem Ordner, der mit der Instanz verknüpft ist. Z. B. Wenn Sie R Services auf der Standardinstanz installiert haben, sind die R-Bibliotheken in diesem Ordner befinden sich standardmäßig:

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library

Auf ähnliche Weise würden verknüpft ist, mit der Standardinstanz von R Tools im Ordner "vorhanden, um" befinden sich standardmäßig werden:

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin

Weitere Informationen darüber, wie Microsoft R eine basisverteilung von R unterscheidet, die Sie aus CRAN erhalten, finden Sie unter [Interoperabilität mit R-Sprache und Microsoft R-Produkte und Features](https://docs.microsoft.com/r-server/what-is-r-server-interoperability)

### <a name="additional-r-packages-from-microsoft-r"></a>Zusätzliche R-Pakete von Microsoft R

Zusätzlich zu der basisverteilung von R [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] enthält einige proprietären R-Pakete als auch ein Framework für die parallele Ausführung von R, die auch die Ausführung von R in remotecomputekontexten unterstützt.

Dieser kombinierte R-Funktionssatz - die R-Basis-Verteilung sowie verbesserte R-Funktionen und -Pakete - werden **Microsoft R** genannt. Wenn Sie Microsoft R-Server (eigenständig) installieren, erhalten Sie genau den gleichen Paketsatz, der mit SQL Server-R-Services (in der Datenbank) installiert wird, aber in einem anderen Ordner.

Microsoft R enthält eine Verteilung von Intel Math Kernel-Bibliothek, die nach Möglichkeit für eine schnellere mathematische Verarbeitung verwendet wird. Beispielsweise wird die einfache lineare Algebra (BLAS)-Bibliothek für viele der Add-On-Pakete sowie von R selbst verwendet. Weitere Informationen dazu finden Sie in diesen Artikeln:

+ [Wie der Intel Math Kernel R beschleunigt](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html)
+ [Die Leistungsvorteile bei der Verknüpfung von R mit Multithread-Math-Bibliotheken](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html)

Zu den wichtigsten Ergänzungen zu Microsoft R gehören die **RevoScaleR**- und **RevoPemaR**-Pakete. Dies sind die R-Pakete, die für eine bessere Leistung größtenteils in C oder C++ geschrieben wurden.

+ **RevoScaleR.** Enthält eine Reihe von APIs für die Bearbeitung von Daten und Analysen. Die APIs wurden optimiert, um Datensätze zu analysieren, die zu groß sind, um in den Arbeitsspeicher zu passen und Berechnungen über mehrere Kerne oder Prozessoren verteilt auszuführen.

   Die RevoScaleR-APIs unterstützen auch die Arbeit mit Teilmengen von Daten für eine höhere Skalierbarkeit. Anders gesagt können die meisten RevoScaleR-Funktionen Datenmengen verarbeiten und die aktualisierten Algorithmen verwenden, um Ergebnisse zu aggregieren. Aus diesem Grund können R-Lösungen, die auf den RevoScaleR-Funktionen beruhen, mit sehr großen Datenmengen arbeiten und sind nicht durch den lokalen Arbeitsspeicher gebunden.

  Das RevoScaleR-Paket unterstützt auch das .XDF-Dateiformat für schnellere Bewegungen und die Speicherung von Daten, die für die Analyse verwendet werden. Das XDF-Format verwendet die spaltenweise Speicherung, ist übertragbar und kann zum Laden und anschließend zum Ändern der Daten aus verschiedenen Quellen, z.B. Text, SPSS oder eine ODBC-Verbindung verwendet werden. 

+ **RevoPemaR.** PEMA steht für Parallel External Memory Algorithm. Das **RevoPemaR**-Paket bietet APIs, die Sie verwenden können, um eigene parallele Algorithmen zu entwickeln. Weitere Informationen finden Sie unter [Handbuch für die ersten Schritte mit RevoPemaR](https://docs.microsoft.com/r-server/r/how-to-developer-pemar).

Zudem wird empfohlen, dass Sie versuchen [MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package), ein neues Paket aus, die unterstützt die Remoteausführung von R-Code und skalierbare, verteilte Verarbeitung Microsoft R, mit verbesserter Machine learning-Algorithmen von Microsoft Research entwickelte.

## <a name="next-steps"></a>Nächste Schritte

[Übersicht über die Architektur](../../advanced-analytics/r/architecture-overview-sql-server-r.md)

[Zur Unterstützung von R-Komponenten in SQL Server](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md)

[Sicherheitsübersicht](../../advanced-analytics/r/security-overview-sql-server-r.md)

