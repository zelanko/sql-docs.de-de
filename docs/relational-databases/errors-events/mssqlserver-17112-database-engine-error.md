---
description: MSSQLSERVER_17112
title: MSSQLSERVER_17112
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.reviewer: ramakoni1, pijocoder, suresh-kandoth, Masha
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17112 (Database Engine error)
ms.assetid: ''
author: suresh-kandoth
ms.author: ramakoni
ms.openlocfilehash: 870f9b9f4d3fcc8186ed1d16faee861ed63e4135
ms.sourcegitcommit: ead0b8c334d487a07e41256ce5d6acafa2d23c9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92418723"
---
# <a name="mssqlserver_17112"></a>MSSQLSERVER_17112
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

## <a name="details"></a>Details

|attribute|Wert|
|---|---|
|Produktname|SQL Server|
|Ereignis-ID|17112|
|Ereignisquelle|MSSQLSERVER|
|Komponente|SQLEngine|
|Symbolischer Name|INIT_INVCOMMAND|
|Meldungstext|Die ungültige Startoption a wurde aus der Registrierung oder an der Befehlszeile bereitgestellt. Korrigieren oder entfernen Sie die Option.|
||

## <a name="explanation"></a>Erklärung

Dieser Fehler weist darauf hin, dass eine ungültige [Startoption für den Datenbank-Engine-Dienst](/sql/database-engine/configure-windows/database-engine-service-startup-options) angegeben wurde. Wenn eine Startoption nicht ordnungsgemäß angegeben ist, kann SQL Server entweder nicht gestartet werden oder wird möglicherweise nicht erwartungsgemäß ausgeführt. Außerdem wird der Fehler 17112 ausgelöst.

In einigen Fällen wird die Instanz möglicherweise gestartet, aber wenn Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll überprüfen, sehen die Startparameter nicht richtig aus:

> \<Datetime> Server Registry startup parameters (<Datetime>-Server-Registrierungsstartparameter):  
\<Datetime>-Server -d D:\Programme\Microsoft SQL Server\MSSQL.1\MSSQL\DATA\master.mdf  
\<Datetime>-Server -e D:\Programme\Microsoft SQL Server\MSSQL.1\MSSQL\LOG\ERRORLOG  
\<Datetime>-Server -l D:\Programme\Microsoft SQL Server\MSSQL.1\MSSQL\DATA\mastlog.ldf  
\<Datetime>-Server -T1118 -g512

Beachten Sie, dass sich die letzten beiden Startparameter in derselben Zeile befinden.

In einigen Fällen stellen Sie möglicherweise auch fest, dass das Hinzufügen der erforderlichen Startparameter nicht die beabsichtigte Auswirkung auf das Serververhalten hatte.

## <a name="possible-causes"></a>Mögliche Ursachen

Diese Probleme treten aus den folgenden Gründen auf:

- Es wurden Startparameter verwendet, die in der gültigen Liste der Startparameter nicht aufgeführt sind.
- Die Startparameter wurden ohne die richtigen Trennzeichen [;] angegeben.
- Die Startparameter wurden aus Text-Editoren kopiert und eingefügt, die einige unsichtbare Sonderzeichen [z. B. ein Leerzeichen vor „-T“] hinzugefügt haben.
- Für den Startparameter wird nicht die richtige Einstellung für die Berücksichtigung von Groß-/Kleinschreibung verwendet.

## <a name="user-action"></a>Benutzeraktion

Verwenden Sie das Tool [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager, um die für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz angegebenen Startparameter bereitzustellen und zu überprüfen. Stellen Sie sicher, dass jeder der Startparameter über das richtige Trennzeichen verfügt und keine Sonderzeichen vorhanden sind.

## <a name="more-information"></a>Weitere Informationen

Weitere Informationen zu diesem Thema finden Sie in den folgenden Artikeln:

- [Startoptionen für den Datenbank-Engine-Dienst](/sql/database-engine/configure-windows/database-engine-service-startup-options)
- [SCM-Dienste: Konfigurieren der Serverstartoptionen](/sql/database-engine/configure-windows/scm-services-configure-server-startup-options)
