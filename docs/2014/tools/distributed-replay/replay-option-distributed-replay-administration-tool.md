---
title: Option „replay“ (Distributed Replay-Verwaltungstool) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: a3114d7c2a2a7908e4e010fbf5d80c7d332d264c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011616"
---
# <a name="replay-option-distributed-replay-administration-tool"></a>Option Wiedergabe (Verwaltungstool Distributed Replay)
  Das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay Verwaltungs Tool, `DReplay.exe` , ist ein Befehlszeilen Tool, das Sie für die Kommunikation mit dem verteilten Replay-Controller verwenden können. In diesem Thema werden die **replay** -Befehlszeilenoption und die entsprechende Syntax beschrieben.

 Die **replay** -Option initiiert die Ereigniswiedergabephase, in der der Controller Wiedergabedaten an die angegebenen Clients weiterleitet, die verteilte Wiedergabe startet und die Clients synchronisiert. Optional kann jeder Client, der an der Wiedergabe teilnimmt, die Wiedergabeaktivität aufzeichnen und eine Ergebnisdatei der Ablaufverfolgung lokal speichern.

 ![Artikellinksymbol](../../database-engine/media/topic-link.gif "Symbol für Themenlink") Weitere Informationen zu den Syntaxkonventionen für das Verwaltungstool finden Sie unter [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Syntax

```

      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]
    [-starget_server] -wclients [-cconfig_file]
    [-fstatus_interval]
```

#### <a name="parameters"></a>Parameter
 **-m** *Controller* gibt den Computernamen des Controllers an. Sie können mit "`localhost`" oder "`.`" auf den lokalen Computer verweisen.

 Wenn der **-m** -Parameter nicht angegeben ist, wird der lokale Computer verwendet.

 **-d** *controller_working_dir* gibt das Verzeichnis auf dem Controller an, in dem die zwischen Datei gespeichert wird. Der **-d** -Parameter ist erforderlich.

 Es gelten die folgenden Anforderungen:

-   Das Verzeichnis muss sich auf dem Controller befinden.

-   Sie müssen den vollständigen Pfad angeben, der mit einem Laufwerkbuchstaben beginnen muss (z. B. `c:\WorkingDir`).

-   Der Pfad darf nicht mit einem umgekehrten Schrägstrich ("`\`") enden.

-   UNC-Pfade werden nicht unterstützt.

 **-o** Erfasst die Wiedergabe Aktivität der Clients und speichert Sie in einer Ergebnisdatei der Ablauf Verfolgung in dem Pfad, der vom- `<ResultDirectory>` Element in der Client Konfigurationsdatei angegeben wird `DReplayClient.xml` .

 Wenn der **-o** -Parameter nicht angegeben wird, wird die Ergebnisdatei der Ablaufverfolgung nicht generiert. Die Konsolenausgabe gibt am Ende der Wiedergabe Zusammenfassungsinformationen zurück, es sind jedoch keine weiteren Wiedergabestatistiken verfügbar.

 **-s** *target_server* gibt die Ziel Instanz von an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , für die die verteilte Arbeitsauslastung wiedergegeben werden soll. Sie müssen diesen Parameter im folgenden Format angeben: **server_name[\instance name]** .

 Sie können den Zielserver nicht mit "`localhost`" oder "`.`" angeben.

 Der **-s** -Parameter ist nicht erforderlich, wenn das `<Server>` -Element im `<ReplayOptions>` -Abschnitt der Wiedergabekonfigurationsdatei `DReplay.exe.replay.config`angegeben wird.

 Wenn der **-s** -Parameter verwendet wird, wird das `<Server>` -Element im `<ReplayOptions>` -Abschnitt der Wiedergabekonfigurationsdatei ignoriert.

 **-w** *Clients* dieser erforderliche Parameter ist eine durch Trennzeichen getrennte Liste (ohne Leerzeichen), die die Computernamen von Clients angibt, die an der verteilten Wiedergabe teilnehmen sollen. IP-Adressen sind nicht zulässig. Beachten Sie, dass die Clients bereits beim Controller registriert sein müssen.

> [!NOTE]
>  Jeder Client wird beim Starten des Clientdiensts bei dem Controller registriert, der in der Clientkonfigurationsdatei angegeben ist.

 der **-c-** *Config_file* ist der vollständige Pfad der Wiedergabe Konfigurationsdatei. wird verwendet, um den Speicherort anzugeben, an dem er an einem anderen Speicherort gespeichert wird.

 Der **-c** -Parameter ist nicht erforderlich, wenn Sie die Standardwerte der Wiedergabekonfigurationsdatei `DReplay.exe.replay.config`verwenden möchten.

 **-f** *status_interval* gibt die Häufigkeit (in Sekunden) an, mit der der Status angezeigt wird.

 Wenn **-f** nicht angegeben wird, ist das Standardintervall 30 Sekunden.

## <a name="examples"></a>Beispiele
 In diesem Beispiel wird ein Großteil des Verhaltens der verteilten Wiedergabe von der geänderten Wiedergabekonfigurationsdatei `DReplay.exe.replay.config`abgeleitet.

-   Der **-m** -Parameter gibt an, dass ein Computer mit dem Namen `controller1` als Controller fungiert. Der Computername muss angegeben werden, wenn der Controllerdienst auf einem anderen Computer ausgeführt wird.

-   Der **-d** -Parameter gibt den Speicherort der Zwischendatei auf dem Controller im Verzeichnis an ( `c:\WorkingDir`).

-   Der **-o** -Parameter legt fest, dass jeder angegebene Client die Wiedergabeaktivität aufzeichnet und in einer Ergebnisdatei der Ablaufverfolgung speichert. Hinweis: Mit dem `<ResultTrace>`-Element in der Konfigurationsdatei kann angegeben werden, ob Zeilenanzahl und Resultset aufgezeichnet werden.

-   Der **-w** -Parameter gibt an, dass die Computer `client1` bis `client4` als Clients an der verteilten Wiedergabe teilnehmen.

-   Der **-c** -Parameter wird verwendet, um auf die geänderte Konfigurationsdatei `DReplay.exe.replay.config`zu zeigen.

-   Der **-s** -Parameter ist nicht erforderlich, da das `<Server>` -Element im `<ReplayOptions>` -Element der Wiedergabekonfigurationsdatei `DReplay.exe.replay.config`angegeben wird.

 Die Ereigniswiedergabephase wird mit der folgenden Syntax initiiert, wenn das Verwaltungstool und der Controller nicht auf demselben Computer ausgeführt werden:

```
dreplay replay -m controller1 -d c:\WorkingDir -o -w client1,client2,client3,client4 -c c:\DReplay.exe.replay.config
```

 Um einen synchronen Sequenzierungsmodus anzugeben, wird das `<SequencingMode>` -Element der Datei `DReplay.exe.replay.config` auf den Wert `synchronization`festgelegt. Der `<ResultTrace>` -Abschnitt der Wiedergabekonfigurationsdatei wurde geändert, um anzugeben, dass die Zeilenanzahl aufgezeichnet wird. Diese Änderungen werden im folgenden XML-Beispiel gezeigt:

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance</Server>
        <SequencingMode>synchronization</SequencingMode>
        <ConnectTimeScale></ConnectTimeScale>
        <ThinkTimeScale></ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

 Um einen Belastungssequenzierungsmodus anzugeben, wird das `<SequencingMode>` -Element der Datei `DReplay.exe.replay.config` auf den Wert `stress`festgelegt. Das `<ConnectTimeScale>` -Element und das `<ThinkTimeScale>` -Element werden auf den Wert `50` festgelegt (um 50 Prozent anzugeben). Weitere Informationen zu Verbindungszeit und Reaktionszeit finden Sie unter [Konfigurieren von Distributed Replay](configure-distributed-replay.md). Diese Änderungen werden im folgenden XML-Beispiel gezeigt:

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance_name</Server>
        <SequencingMode>stress</SequencingMode>
        <ConnectTimeScale>50</ConnectTimeScale>
        <ThinkTimeScale>50</ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

## <a name="permissions"></a>Berechtigungen
 Sie müssen das Verwaltungstool als interaktiver Benutzer mit einem lokalen Benutzerkonto oder Domänenbenutzerkonto ausführen. Um ein lokales Benutzerkonto zu verwenden, müssen das Verwaltungstool und der Controller auf demselben Computer ausgeführt werden.

 Weitere Informationen finden Sie unter [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>Weitere Informationen
 Wiedergeben von Ablauf [Verfolgungs Daten](replay-trace-data.md) [Überprüfen Sie die Wiedergabe Ergebnisse](review-the-replay-results.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Konfigurieren Distributed Replay](configure-distributed-replay.md) [SQL Server Distributed Replay Forums](https://social.technet.microsoft.com/Forums/sl/sqldru/) [mithilfe Distributed Replay zum Auslastungs Test Ihres SQL Server-Teils 2](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2) [mithilfe Distributed Replay zum Auslastungs Test SQL Server-Teil 1](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1)


