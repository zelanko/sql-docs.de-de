---
title: Option „preprocess“ (Distributed Replay-Verwaltungstool) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 9b5012fd-233e-4a25-a2e1-585c63b70502
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57adcc55cf7b699e5092671fc61eb83278858cb4
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177340"
---
# <a name="preprocess-option-distributed-replay-administration-tool"></a>Vorverarbeitungsoption (Verwaltungstool "Distributed Replay")
  Das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Verwaltungs Tool, `DReplay.exe`, ist ein Befehlszeilen Tool, das Sie für die Kommunikation mit dem verteilten Replay-Controller verwenden können. In diesem Thema werden die Befehlszeilenoption **preprocess** und die entsprechende Syntax beschrieben.

 Die **preprocess** -Option initiiert die Vorverarbeitungsphase. In dieser Phase bereitet der Controller die Eingabedaten der Ablaufverfolgung für die Wiedergabe anhand des Zielservers vor.

 ![Artikellinksymbol](../../database-engine/media/topic-link.gif "Symbol für Themenlink") Weitere Informationen zu den Syntaxkonventionen für das Verwaltungstool finden Sie unter [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Syntax

```

      dreplay preprocess [-mcontroller] -iinput_trace_file
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]
```

#### <a name="parameters"></a>Parameter
 **-m** *Controller* gibt den Computernamen des Controllers an. Sie können mit "`localhost`" oder "`.`" auf den lokalen Computer verweisen.

 Wenn der **-m** -Parameter nicht angegeben ist, wird der lokale Computer verwendet.

 **-i** *input_trace_file* gibt den vollständigen Pfad der Eingabedatei der Ablauf Verfolgung auf dem Controller an `D:\Mytrace.trc`, z. b.. Der **-i** -Parameter ist erforderlich.

 Wenn Rolloverdateien im gleichen Verzeichnis vorhanden sind, werden sie geladen und automatisch verwendet. Die Dateien müssen der Dateirollover-Benennungskonvention folgen, z.B.: `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`, ... `Mytrace_n.trc`.

> [!NOTE]
>  Wenn Sie das Verwaltungstool auf einem anderen Computer als dem Controller verwenden, müssen Sie die Eingabedateien der Ablaufverfolgung auf den Controller kopieren, damit ein lokaler Pfad für diesen Parameter verwendet werden kann.

 **-d** *controller_working_dir* gibt das Verzeichnis auf dem Controller an, in dem die zwischen Datei gespeichert wird. Der **-d** -Parameter ist erforderlich.

 Es gelten die folgenden Anforderungen:

-   Das Verzeichnis muss sich auf dem Controller befinden.

-   Sie müssen den vollständigen Pfad angeben, der mit einem Laufwerkbuchstaben beginnen muss (z. B. `c:\WorkingDir`).

-   Der Pfad darf nicht mit einem umgekehrten Schrägstrich ("`\`") enden.

-   UNC-Pfade werden nicht unterstützt.

 der **-c-** *Config_file* ist der vollständige Pfad der Vorverarbeitungs Konfigurationsdatei. wird verwendet, um den Speicherort der Vorverarbeitungs Konfigurationsdatei anzugeben, wenn Sie an einem anderen Speicherort gespeichert wird. Dieser Parameter kann ein UNC-Pfad sein oder ein lokales Verzeichnis auf dem Computer angeben, auf dem Sie das Verwaltungstool ausführen.

 Der **-c** -Parameter ist nicht erforderlich, wenn keine Filterung benötigt wird oder wenn Sie die maximale Leerlaufzeit nicht ändern möchten.

 Ohne den **-c** -Parameter wird die Standardkonfigurationsdatei für die Vorverarbeitung verwendet: `DReplay.exe.preprocess.config`.

 **-f** *status_interval* gibt die Häufigkeit (in Sekunden) für die Anzeige von Statusmeldungen an.

 Wenn **-f** nicht angegeben wird, ist das Standardintervall 30 Sekunden.

## <a name="examples"></a>Beispiele
 In diesem Beispiel wird die Vorverarbeitungsphase mit allen Standardeinstellungen initiiert. Der Wert `localhost` gibt an, dass der Controllerdienst auf demselben Computer wie das Verwaltungstool ausgeführt wird. Der *input_trace_file* -Parameter gibt den Speicherort der Eingabedaten der Ablaufverfolgung an: `c:\mytrace.trc`. Da keine Filterung der Ablaufverfolgungsdatei erfolgt, muss der **-c** -Parameter angegeben werden.

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir
```

 In diesem Beispiel wird die Vorverarbeitungsphase initiiert, und es wird eine geänderte Vorverarbeitungskonfigurationsdatei angegeben. Im Gegensatz zum vorherigen Beispiel wird der **-c** -Parameter verwendet, um auf die geänderte Konfigurationsdatei zu zeigen, wenn Sie diese an einem anderen Speicherort gespeichert haben. Beispiel:

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir -c c:\DReplay.exe.preprocess.config
```

 Der geänderten Vorverarbeitungskonfigurationsdatei wird eine Filterbedingung hinzugefügt, die während der verteilten Wiedergabe Systemsitzungen herausfiltert. Der Filter wird durch Ändern des `<PreprocessModifiers>` -Elements in der Vorverarbeitungskonfigurationsdatei `DReplay.exe.preprocess.config`hinzugefügt.

 Im folgenden Beispiel wird die geänderte Konfigurationsdatei gezeigt:

```
<?xml version='1.0'?>
<Options>
    <PreprocessModifiers>
        <IncSystemSession>No</IncSystemSession>
        <MaxIdleTime>-1</MaxIdleTime>
    </PreprocessModifiers>
</Options>
```

## <a name="permissions"></a>Berechtigungen
 Sie müssen das Verwaltungstool als interaktiver Benutzer mit einem lokalen Benutzerkonto oder Domänenbenutzerkonto ausführen. Um ein lokales Benutzerkonto zu verwenden, müssen das Verwaltungstool und der Controller auf demselben Computer ausgeführt werden.

 Weitere Informationen finden Sie unter [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>Weitere Informationen
 [Vorbereiten der Eingabedaten der Ablauf Verfolgung](prepare-the-input-trace-data.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Konfigurieren Distributed Replay](configure-distributed-replay.md)


