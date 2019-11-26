---
title: Skalieren von gleichzeitig ausgeführten Skripts
description: Konfigurieren Sie die parallele oder gleichzeitige R- und Python-Skriptausführung in einem Benutzerkontenpool, um SQL Server Machine Learning Services zu skalieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/25/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: c10f92bcb0f8b64441ad4b088c4b8b3e2f62236b
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727702"
---
# <a name="scale-concurrent-execution-of-external-scripts-in-sql-server-machine-learning-services"></a>Skalieren der gleichzeitigen Ausführung externer Skripts in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erfahren Sie mehr über Workerkonten für SQL Server Machine Learning Services und wie Sie die Standardkonfiguration ändern können, um die Anzahl der gleichzeitigen Ausführung externer Skripts zu skalieren.

Im Rahmen des Installationsprozesses für Machine Learning Services wird ein neuer Windows-*Benutzerkontenpool* erstellt, um die Ausführung von Aufgaben vom [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]-Dienst zu unterstützen. Der Zweck dieser Workerkonten ist es, das gleichzeitige Ausführen externer Skripts von verschiedenen SQL Server-Benutzern zu isolieren.

> [!Note]
> In SQL Server 2019 hat **SQLRUserGroup** nur ein Mitglied, das nun das einzige SQL Server-Launchpad-Dienstkonto anstelle von mehreren Workerkonten ist. In diesem Artikel werden die Workerkonten für SQL Server 2016 und 2017 beschrieben.

## <a name="worker-account-group"></a>Workerkontogruppe

Eine Windows-Kontengruppe wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup für jede Instanz erstellt, auf der Machine Learning installiert und aktiviert ist.

- In einer Standardinstanz ist der Gruppenname **SQLRUserGroup**. Der Name bleibt gleich, egal ob Sie Python oder R oder beides verwenden.
- In einer benannten Instanz erhält der Standardgruppenname den Instanznamen als Suffix, z.B. **SQLRUserGroupMyInstanceName**.

Standardmäßig enthält der Benutzerkontenpool 20 Benutzerkonten. In den meisten Fällen sind 20 Konten mehr als ausreichend, um Machine Learning-Tasks zu unterstützen; wenn nötig können Sie die Anzahl der Konten anpassen. Die maximale Anzahl von Konten ist 100.

- In einer Standardinstanz haben die einzelnen Konten Namen von **MSSQLSERVER01** bis **MSSQLSERVER20**.
- In einer benannten Instanz sind die Konten nach dem Instanznamen benannt, z.B **MyInstanceName01** bis **MyInstanceName20**.

Wenn mehr als eine Instanz Machine Learning verwendet, verfügt der Computer über mehrere Benutzergruppen. Eine Gruppe kann nicht von mehreren Instanzen gemeinsam genutzt werden.

<a name = "HowToChangeGroup"> </a>

## <a name="number-of-worker-accounts"></a>Anzahl von Workerkonten

Sie müssen die Eigenschaften des [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]-Dienstes wie unten beschrieben ändern, um die Anzahl der Benutzer im Kontenpool zu ändern.

Die jeweiligen Kennwörter der Benutzerkonten werden nach dem Zufallsprinzip generiert. Sie können Sie zu einem späteren Zeitpunkt ändern, nachdem die Konnten erstellt wurden.

1. Klicken Sie im SQL Server Configuration Manager auf **SQL Server-Dienste**.
2. Doppelklicken Sie auf den Launchpad-Dienst von SQL Server und beenden Sie den Dienst, wenn er ausgeführt wird.
3.  Achten Sie darauf, dass der Startmodus auf der Registerkarte **Dienst** auf „Automatisch“ festgelegt ist. Externe Skripts können nicht gestartet werden, wenn das Launchpad nicht ausgeführt wird.
4.  Klicken Sie auf die Registerkarte **Erweitert**, und bearbeiten Sie den Wert von **External Users Count** (Anzahl externer Benutzer), wenn nötig. Diese Einstellung steuert, wie viele verschiedene SQL-Benutzer gleichzeitig externe Skriptsitzungen ausführen können. Der Standard sind 20 Konten. Die maximale Anzahl der Benutzer beträgt 100.
5. Sie können die Option **Reset External Users Password** (Kennwörter externer Benutzer zurücksetzen) auch wahlweise auf _Ja_ festlegen, wenn Ihre Organisation eine Richtlinie zum regelmäßigen Ändern des Kennworts hat. Damit werden die verschlüsselten Kennwörter erneut generiert, die Launchpad für die Benutzerkonten verwaltet. Weitere Informationen finden Sie unter [Enforcing Password Policy (Erzwingen der Kennwortrichtlinie)](../security/sql-server-launchpad-service-account.md#bkmk_EnforcePolicy).
6.  Starten Sie den Launchpad-Dienst neu.

## <a name="managing-workloads"></a>Verwalten von Arbeitsauslastungen

Die Anzahl von Konten in diesem Pool bestimmt, wie viele externe Skriptsitzungen gleichzeitig aktiv sein können.  Standardmäßig werden 20 Konten erstellt, d. h., dass 20 verschiedene Benutzer zur gleichen Zeit aktive Python- oder R-Sitzungen haben können. Sie können die Anzahl der Workerkonten erhöhen, wenn Sie erwarten, dass Sie mehr als 20 Skripts gleichzeitig auszuführen werden.

Wenn der gleiche Benutzer mehrere externe Skripts gleichzeitig ausführt, verwenden alle von diesem Benutzer ausgeführten Sitzungen das gleiche Workerkonto. Ein einzelner Benutzer kann z. B. 100 verschiedene Python- und R-Skripts gleichzeitig ausführen, solange die Ressourcen es zulassen, dabei würden jedoch alle Skripts mit einem einzelnen Workerkonto ausgeführt.

Die Anzahl von Workerkonten, die Sie unterstützen können, und die Anzahl von gleichzeitigen Sitzungen, die ein einzelner Benutzer ausführen kann, werden nur durch Serverressourcen eingeschränkt. Für gewöhnlich ist der Arbeitsspeicher der erste Engpass beim Verwenden der Python- oder R-Laufzeit.

Die Ressourcen, die von Python- oder R-Skripts verwendet werden können, werden von SQL Server gesteuert. Es wird empfohlen, dass Sie die Ressourcenauslastung mit SQL Server DMVs überwachen oder sich Leistungsindikatoren im verknüpften Windows-Auftragsobjekt anschauen; so können Sie die Arbeitsspeicherauslastung des Servers entsprechend anpassen. Wenn Sie SQL Server Enterprise Edition verwenden, können Sie Ressourcen für das Ausführen von externen Skripts zuweisen, indem Sie einen [externen Ressourcenpool](how-to-create-a-resource-pool.md) konfigurieren.

## <a name="next-steps"></a>Nächste Schritte

- [Überwachen der Python- und R-Skriptausführung mithilfe von benutzerdefinierten Berichten in SQL Server Management Studio](../../advanced-analytics/administration/monitor-sql-server-machine-learning-services-using-custom-reports-management-studio.md)
- [Überwachen von SQL Server Machine Learning Services mithilfe von dynamischen Verwaltungssichten (DMVs)](../../advanced-analytics/administration/monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)