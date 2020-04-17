---
title: Benutzerdefinierte CLR-Typen | Microsoft Docs
description: In diesem Artikel wird der Prozess zum Erstellen benutzerdefinierter Typen (UDTs) zum Speichern von CLR-Objekten in einer SQL Server-Datenbank beschrieben.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: b3983459ac8ca4b38c82cc926c2f1b0f55bb1d58
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487859"
---
# <a name="clr-user-defined-types"></a>Benutzerdefinierte CLR-Typen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ermöglicht das Erstellen von Datenbankobjekten, die für eine Assembly programmiert sind, die in der .NET Framework Common Language Runtime (CLR) erstellt wurde. Zu den Datenbankobjekten, die das umfangreiche Programmierungsmodell der CLR nutzen können, zählen Trigger, gespeicherte Prozeduren, Funktionen, Aggregatfunktionen und Typen.  
  
> [!NOTE]  
>  Die Möglichkeit zum Ausführen von CLR-Code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist standardmäßig in auf OFF festgelegt. Die CLR kann mithilfe der **sp_configure** gespeicherten Systemprozedur aktiviert werden.  
  
 Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], können Sie benutzerdefinierte Typen (UDTs) verwenden, um das Skalartypsystem des Servers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu erweitern und die Speicherung von CLR-Objekten in einer Datenbank zu ermöglichen. UDTs können mehrere Elemente enthalten und Verhalten zeigen, das sie von den herkömmlichen Aliasdatentypen unterscheidet, die aus einem einzelnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatentyp bestehen.  
  
 Da das System auf UDTs als Ganzes zugreift, kann sich ihre Verwendung für komplexe Datentypen negativ auf die Leistung auswirken. Komplexe Daten werden im Allgemeinen am besten mit herkömmlichen Zeilen und Tabellen modelliert. UDTs sind in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für folgende Zwecke geeignet:  
  
-   Datum, Zeit, Währung und erweiterte numerische Typen  
  
-   Geospatial-Anwendungen  
  
-   Codierte oder verschlüsselte Daten  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] besteht der Prozess der UDTs-Entwicklung aus den folgenden Schritten:  
  
1.  **Codieren und erstellen Sie die Assembly, die den UDT definiert.** UDTs werden in einer beliebigen, von der .NET Framework-CLR (Common Language Runtime) unterstützten Sprache definiert, die überprüfbaren Code generiert. Dazu gehören Visual C- und Visual Basic .NET. Die Daten werden in Feldern und Eigenschaften einer .NET Framework-Klasse oder -Struktur verfügbar gemacht. Das Verhalten wird durch die Methoden der Klasse oder Struktur definiert.  
  
2.  **Registrieren Sie die Assembly.** UDTs können über die Visual Studio-Benutzeroberfläche in einem Datenbankprojekt oder mit der[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung CREATE ASSEMBLY bereitgestellt werden, die die Assembly, die die Klasse oder Struktur enthält, in eine Datenbank kopiert.  
  
3.  **Erstellen Sie den UDT in SQL Server.** Sobald eine Assembly in eine Hostdatenbank geladen wurde, erstellen Sie einen UDT mit der  [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung CREATE TYPE, und machen die Elemente der Klasse oder Struktur als Elemente des UDT verfügbar. UDTs sind nur im Kontext einer einzelnen Datenbank vorhanden und weisen nach der Registrierung keine Abhängigkeiten mehr von den externen Dateien auf, aus denen sie erstellt wurden.  
  
    > [!NOTE]  
    >  Vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] wurden aus .NET Framework-Assemblys erstellte UDTs nicht unterstützt. Sie können jedoch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weiterhin Aliasdatentypen verwenden, indem Sie **sp_addtype**verwenden. Die CREATE TYPE-Syntax kann zum Erstellen sowohl von systemeigenen, benutzerdefinierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen als auch UDTs verwendet werden.  
  
4.  **Erstellen von Tabellen, Variablen oder Parametern mithilfe der UDT** Beginnend [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]mit kann ein benutzerdefinierter Typ als Spaltendefinition einer Tabelle, [!INCLUDE[tsql](../../includes/tsql-md.md)] als Variable in einem [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch oder als Argument einer Funktion oder gespeicherten Prozedur verwendet werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen eines benutzerdefinierten Typs](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
 Beschreibt das Erstellen von UDTs.  
  
 [Registrieren benutzerdefinierter Typen in SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/registering-user-defined-types-in-sql-server.md)  
 Beschreibt, wie UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert und verwaltet werden.  
  
 [Arbeiten mit benutzerdefinierten Typen in SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
 Beschreibt das Erstellen von Abfragen mit UDTs.  
  
 [Zugreifen auf benutzerdefinierte Typen in ADO.NET](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
 Beschreibt die Verwendung von UDTs mit dem .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in ADO.NET.  
  
  
