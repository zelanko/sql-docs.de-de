---
title: Skalieren der gleichzeitigen Ausführung externer Skripts
description: Konfigurieren Sie die parallele oder gleichzeitige R-und python-Skriptausführung in einem Benutzerkonten Pool, um SQL Server Machine Learning Services zu skalieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e44137b539b24bc6cdb8fc55f2df2877c19babe2
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344026"
---
# <a name="scale-concurrent-execution-of-external-scripts-in-sql-server-machine-learning-services"></a>Skalieren der gleichzeitigen Ausführung externer Skripts in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Im Rahmen des Installationsprozesses für [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] wird ein neuer Windows-*Benutzerkontenpool* erstellt, um die Ausführung von Aufgaben vom [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]-Dienst zu unterstützen. Der Zweck dieser workerkonten ist die Isolierung der gleichzeitigen Ausführung externer Skripts durch verschiedene SQL-Benutzer.

Dieser Artikel beschreibt die Standardkonfiguration und-Kapazität für die workerkonten und zeigt, wie die Standardkonfiguration geändert wird, um die Anzahl der gleichzeitigen Ausführung externer Skripts in SQL Server Machine Learning Services zu skalieren.

## <a name="worker-account-group"></a>Worker-Konto Gruppe

Eine Windows-Konto Gruppe wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup für jede Instanz erstellt, auf der Machine Learning installiert und aktiviert ist.

- In einer Standardinstanz ist der Gruppenname **SQLRUserGroup**. Der Name ist identisch, unabhängig davon, ob Sie R oder python oder beides verwenden.
- In einer benannten Instanz erhält der Standardgruppenname den Instanznamen als Suffix, z.B. **SQLRUserGroupMyInstanceName**.

Standardmäßig enthält der Benutzerkontenpool 20 Benutzerkonten. In den meisten Fällen sind 20 mehr als ausreichend, um Machine Learning-Aufgaben zu unterstützen, aber Sie können die Anzahl der Konten ändern. Die maximale Anzahl von Konten ist 100.

- In einer Standardinstanz haben die einzelnen Konten Namen von **MSSQLSERVER01** bis **MSSQLSERVER20**.
- In einer benannten Instanz sind die Konten nach dem Instanznamen benannt, z.B **MyInstanceName01** bis **MyInstanceName20**.

Wenn mehr als eine Instanz Machine Learning verwendet, verfügt der Computer über mehrere Benutzergruppen. Eine Gruppe kann nicht zwischen Instanzen freigegeben werden.

> [!Note]
> In SQL Server 2019 verfügt **sqlrusergroup** nur über einen Member, bei dem es sich um das einzige SQL Server-Launchpad Dienst Konto anstelle mehrerer workerkonten handelt.

<a name = "HowToChangeGroup"> </a>

## <a name="number-of-worker-accounts"></a>Anzahl von workerkonten

Sie müssen die Eigenschaften des [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]-Dienstes wie unten beschrieben ändern, um die Anzahl der Benutzer im Kontenpool zu ändern.

Die jeweiligen Kennwörter der Benutzerkonten werden nach dem Zufallsprinzip generiert. Sie können Sie zu einem späteren Zeitpunkt ändern, nachdem die Konnten erstellt wurden.

1. Klicken Sie im SQL Server Configuration Manager auf **SQL Server-Dienste**.
2. Doppelklicken Sie auf den Launchpad-Dienst von SQL Server und beenden Sie den Dienst, wenn er ausgeführt wird.
3.  Achten Sie darauf, dass der Startmodus auf der Registerkarte **Dienst** auf „Automatisch“ festgelegt ist. Externe Skripts können nicht gestartet werden, wenn das Launchpad nicht ausgeführt wird.
4.  Klicken Sie auf die Registerkarte **Erweitert**, und bearbeiten Sie den Wert von **External Users Count** (Anzahl externer Benutzer), wenn nötig. Mit dieser Einstellung wird gesteuert, wie viele verschiedene SQL-Benutzer externe Skript Sitzungen gleichzeitig ausführen können. Der Standardwert ist 20 Konten. Die maximale Anzahl von Benutzern beträgt 100.
5. Sie können die Option **Reset External Users Password** (Kennwörter externer Benutzer zurücksetzen) auch wahlweise auf _Ja_ festlegen, wenn Ihre Organisation eine Richtlinie zum regelmäßigen Ändern des Kennworts hat. Damit werden die verschlüsselten Kennwörter erneut generiert, die Launchpad für die Benutzerkonten verwaltet. Weitere Informationen finden Sie unter [Enforcing Password Policy (Erzwingen der Kennwortrichtlinie)](../security/sql-server-launchpad-service-account.md#bkmk_EnforcePolicy).
6.  Starten Sie den Launchpad-Dienst neu.

## <a name="managing-workloads"></a>Verwalten von Workloads

Die Anzahl der Konten in diesem Pool bestimmt, wie viele externe Skript Sitzungen gleichzeitig aktiv sein können.  Standardmäßig werden 20 Konten erstellt. Dies bedeutet, dass 20 verschiedene Benutzer gleichzeitig über aktive R-oder python-Sitzungen verfügen können. Sie können die Anzahl von workerkonten erhöhen, wenn Sie erwarten, dass mehr als 20 gleichzeitige Skripts ausgeführt werden.

Wenn derselbe Benutzer mehrere externe Skripts gleichzeitig ausführt, wird für alle von diesem Benutzer ausgeführten Sitzungen dasselbe Workerkonto verwendet. Beispielsweise kann für einen einzelnen Benutzer 100 verschiedene R-Skripts gleichzeitig ausgeführt werden, solange die Ressourcen zulässig sind, aber alle Skripts werden mit einem einzigen Workerkonto ausgeführt.

Die Anzahl von workerkonten, die Sie unterstützen können, und die Anzahl der gleichzeitigen Sitzungen, die ein einzelner Benutzer ausführen kann, wird nur durch Server Ressourcen beschränkt. Für gewöhnlich ist der Arbeitsspeicher der erste Engpass beim Verwenden der R-Laufzeit.

Die Ressourcen, die von Python-oder R-Skripts verwendet werden können, werden SQL Server gesteuert. Es wird empfohlen, dass Sie die Ressourcenauslastung mit SQL Server DMVs überwachen oder sich Leistungsindikatoren im verknüpften Windows-Auftragsobjekt anschauen; so können Sie die Arbeitsspeicherauslastung des Servers entsprechend anpassen. Wenn Sie über SQL Server Enterprise Edition verfügen, können Sie Ressourcen zuweisen, die zum Ausführen externer Skripts verwendet werden, indem Sie einen [externen Ressourcenpool](how-to-create-a-resource-pool.md)konfigurieren.

## <a name="see-also"></a>Siehe auch

Weitere Informationen zum Konfigurieren der Kapazität finden Sie in den folgenden Artikeln:

- [SQL Server Konfiguration für R Services](../../advanced-analytics/r/sql-server-configuration-r-services.md)
- [Leistungs Fallstudie für R Services](../../advanced-analytics/r/performance-case-study-r-services.md)