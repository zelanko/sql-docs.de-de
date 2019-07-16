---
title: Gleichzeitige Ausführung externer Skripts – SQL Server-Machine Learning-Dienste skalieren
description: Konfigurieren von parallel oder gleichzeitigen R und Python-Skript die Ausführung in einer benutzerkontenpool zum Skalieren von SQL Server-Machine Learning-Dienste.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: b672ce067d5d1f10754f346c77967b4e3fbe34ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963169"
---
# <a name="scale-concurrent-execution-of-external-scripts-in-sql-server-machine-learning-services"></a>Gleichzeitige Ausführung externer Skripts in SQL Server-Machine Learning-Dienste skalieren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Im Rahmen des Installationsprozesses für [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] wird ein neuer Windows-*Benutzerkontenpool* erstellt, um die Ausführung von Aufgaben vom [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]-Dienst zu unterstützen. Der Zweck dieser workerkonten ist es, gleichzeitige Ausführung externer Skripts, die von verschiedenen SQL-Benutzern zu isolieren.

Dieser Artikel beschreibt die Standardkonfiguration und die Kapazität für die workerkonten und zum Ändern der Standardkonfiguration, um die Anzahl der gleichzeitigen Ausführung externer Skripts in SQL Server-Machine Learning-Dienste zu skalieren.

## <a name="worker-account-group"></a>Konto-workergruppe

Eine Gruppe der Windows-Konto wird erstellt, indem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup für jede Instanz auf dem Machine Learning installiert und aktiviert ist.

- In einer Standardinstanz ist der Gruppenname **SQLRUserGroup**. Der Name ist gleich, ob Sie R, Python oder beides verwenden.
- In einer benannten Instanz erhält der Standardgruppenname den Instanznamen als Suffix, z.B. **SQLRUserGroupMyInstanceName**.

Standardmäßig enthält der Benutzerkontenpool 20 Benutzerkonten. Klicken Sie in den meisten Fällen 20 ist mehr als ausreichend, um Machine Learning-Aufgaben unterstützen, aber Sie können die Anzahl der Konten ändern. Die maximale Anzahl von Konten ist 100.

- In einer Standardinstanz haben die einzelnen Konten Namen von **MSSQLSERVER01** bis **MSSQLSERVER20**.
- In einer benannten Instanz sind die Konten nach dem Instanznamen benannt, z.B **MyInstanceName01** bis **MyInstanceName20**.

Wenn mehr als eine Instanz Machine Learning verwendet wird, wird der Computer mehrere Benutzergruppen sein. Eine Gruppe kann nicht zwischen Instanzen freigegeben werden.

> [!Note]
> In SQL Server-2019 **SQLRUserGroup** hat nur ein Element handelt es sich nun die einzelnen SQL Server Launchpad-Dienstkonto anstelle mehrerer Konten.

<a name = "HowToChangeGroup"> </a>

## <a name="number-of-worker-accounts"></a>Anzahl von workerkonten

Sie müssen die Eigenschaften des [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]-Dienstes wie unten beschrieben ändern, um die Anzahl der Benutzer im Kontenpool zu ändern.

Die jeweiligen Kennwörter der Benutzerkonten werden nach dem Zufallsprinzip generiert. Sie können Sie zu einem späteren Zeitpunkt ändern, nachdem die Konnten erstellt wurden.

1. Klicken Sie im SQL Server Configuration Manager auf **SQL Server-Dienste**.
2. Doppelklicken Sie auf den Launchpad-Dienst von SQL Server und beenden Sie den Dienst, wenn er ausgeführt wird.
3.  Achten Sie darauf, dass der Startmodus auf der Registerkarte **Dienst** auf „Automatisch“ festgelegt ist. Externe Skripts können nicht gestartet werden, wenn das Launchpad nicht ausgeführt wird.
4.  Klicken Sie auf die Registerkarte **Erweitert**, und bearbeiten Sie den Wert von **External Users Count** (Anzahl externer Benutzer), wenn nötig. Diese Einstellung steuert können wie viele verschiedene SQL-Benutzer externen Skript Sitzungen gleichzeitig ausführen. Der Standardwert ist 20 Konten. Die maximale Anzahl von Benutzern ist 100.
5. Sie können die Option **Reset External Users Password** (Kennwörter externer Benutzer zurücksetzen) auch wahlweise auf _Ja_ festlegen, wenn Ihre Organisation eine Richtlinie zum regelmäßigen Ändern des Kennworts hat. Damit werden die verschlüsselten Kennwörter erneut generiert, die Launchpad für die Benutzerkonten verwaltet. Weitere Informationen finden Sie unter [Enforcing Password Policy (Erzwingen der Kennwortrichtlinie)](../security/sql-server-launchpad-service-account.md#bkmk_EnforcePolicy).
6.  Starten Sie den Launchpad-Dienst neu.

## <a name="managing-workloads"></a>Verwalten von workloads

Die Anzahl der Konten in diesem Pool bestimmt, wie viele externes Skript-Sitzungen gleichzeitig aktiv sein können.  Standardmäßig werden 20 Konten erstellt, was bedeutet, dass 20 verschiedene Benutzer aktive R oder Python Sitzungen gleichzeitig verfügen können. Sie können die Anzahl der workerkonten erhöhen, dass Sie voraussichtlich mehr als 20 gleichzeitige Skripts ausgeführt werden.

Wenn die gleiche Benutzer mehrere externe Skripts gleichzeitig ausführt, verwenden Sie alles, was die Sitzungen von diesem Benutzer ausgeführten das gleiche workerkonto. Ein einzelner Benutzer möglicherweise z.B. 100 verschiedene R-Skripts, die gleichzeitig ausgeführt werden, solange die Ressourcen die zulassen, aber alle Skripts werden mit einem einzelnen workerkonto ausführen.

Die Anzahl der workerkonten, die Sie unterstützen können, und die Anzahl gleichzeitiger Sitzungen, die ein einzelner Benutzer ausgeführt werden kann, wird nur durch Serverressourcen eingeschränkt. Für gewöhnlich ist der Arbeitsspeicher der erste Engpass beim Verwenden der R-Laufzeit.

Die Ressourcen, die von Python- oder R-Skripts verwendet werden können, werden von SQL Server gesteuert. Es wird empfohlen, dass Sie die Ressourcenauslastung mit SQL Server DMVs überwachen oder sich Leistungsindikatoren im verknüpften Windows-Auftragsobjekt anschauen; so können Sie die Arbeitsspeicherauslastung des Servers entsprechend anpassen. Wenn Sie SQL Server Enterprise Edition haben, können Sie für die Ausführung externer Skripts durch Konfigurieren von Ressourcen zuordnen einer [externen Ressourcenpool](how-to-create-a-resource-pool.md).

## <a name="see-also"></a>Siehe auch

Weitere Informationen zum Konfigurieren der Kapazität finden Sie in diesen Artikeln:

- [SQL Server-Konfiguration für R Services](../../advanced-analytics/r/sql-server-configuration-r-services.md)
- [Leistungsfallstudie für R Services](../../advanced-analytics/r/performance-case-study-r-services.md)