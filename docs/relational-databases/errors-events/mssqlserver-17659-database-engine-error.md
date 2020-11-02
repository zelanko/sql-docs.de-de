---
description: MSSQLSERVER_17659
title: MSSQLSERVER_17659
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.reviewer: ramakoni1, pijocoder, suresh-kandoth, Masha
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17659 (Database Engine error)
ms.assetid: ''
author: suresh-kandoth
ms.author: ramakoni
ms.openlocfilehash: 5e4656c437e1b1a19382222107add8392e0c47e4
ms.sourcegitcommit: ead0b8c334d487a07e41256ce5d6acafa2d23c9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92418718"
---
# <a name="mssqlserver_17659"></a>MSSQLSERVER_17659
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

## <a name="details"></a>Details

|attribute|Wert|
|---|---|
|Produktname|SQL Server|
|Ereignis-ID|17659|
|Ereignisquelle|MSSQLSERVER|
|Komponente|SQLEngine|
|Symbolischer Name|DEMO_SYSCATUPDATE|
|Meldungstext|Die Systemtabelle mit der ID \%d in der Datenbank mit der ID \%d wurde direkt aktualisiert. Die Cachekohärenz ist möglicherweise verloren gegangen. <br/> SQL Server sollte neu gestartet werden.|
||

## <a name="explanation"></a>Erklärung

Dieser Fehler deutet darauf hin, dass ein Systemobjekt direkt aktualisiert wurde. Das manuelle Aktualisieren von Systemtabellen wird nicht unterstützt. Die Systemtabellen sollten nur von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank-Engine aktualisiert werden. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Benutzern initiierte Änderungen an den Systemtabellen erkennt, wird der Fehler 17659 ausgelöst: Ein Ereignis, das dem folgenden ähnelt, wird im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll oder im Anwendungsprotokoll in der Ereignisanzeige in diesem Szenario protokolliert.

> Protokollname: Application  
Quelle: MSSQLServer  
Ereignis-ID: 17659  
Taskkategorie: Server  
Ebene: Information  
Beschreibung: Warnung: Die Systemtabelle mit der ID \%d in der Datenbank mit der ID %d wurde direkt aktualisiert. Die Cachekohärenz ist möglicherweise verloren gegangen. SQL Server sollte neu gestartet werden.

## <a name="user-action"></a>Benutzeraktion

Sie können dieses Problem mit einer der folgenden Methoden beheben:

- Methode 1  
    Wenn Sie über eine fehlerfreie Sicherung der Datenbank verfügen, stellen Sie die Datenbank aus dieser wieder her.  
    > [!NOTE]
    > Diese Methode funktioniert nur, wenn die Sicherung keine Inkonsistenzen in den Metadaten aufweist.  

- Methode 2  
    Wenn Sie die Datenbank nicht aus einer Sicherung wiederherstellen können, exportieren Sie die Daten und Objekte in eine neue Datenbank. Übertragen Sie dann den Inhalt der manuell aktualisierten Datenbank in die neue Datenbank. Hinweis: Sie können Inkonsistenzen in den Systemkatalogen nicht mithilfe der REPAIR-Optionen in den DBCC CHECKDB-Befehlen beheben. Da der Befehl keine Metadatenfehler beheben kann, weist er keine der empfohlenen Reparaturstufen auf.

> [!NOTE]
> Sie können die Daten in den Systemtabellen über die Systemkatalogsichten abrufen.

## <a name="more-information"></a>Weitere Informationen

Weitere Informationen finden Sie unter: [Systembasistabellen](/sql/relational-databases/system-tables/system-base-tables).
