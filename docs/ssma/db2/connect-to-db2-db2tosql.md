---
title: Verbinden mit DB2 (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9d485fd0-ab5d-402a-a59a-e9982a61b7de
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ab734e93743d3a3158feb16dba044b58e7f48f23
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299155"
---
# <a name="connect-to-db2-db2tosql"></a>Verbinden mit DB2 (DB2ToSQL)
Verwenden der **Herstellen einer Verbindung mit DB2** im Dialogfeld Verbindung mit der DB2-Datenbank, die Sie migrieren möchten.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit DB2**. Wenn Sie zuvor eine Verbindung hergestellt haben, wird der Befehl ist **Wiederherstellen der Verbindung mit DB2**.  
  
## <a name="options"></a>Optionen  
**Anbieter**  
Wählen Sie den Access-Datenanbieter für die Verbindung mit der DB2-Datenbank. Verfügbare Anbieter sind den DB2-Client-Anbieter und der OLE DB-Anbieter. Der Standardwert ist die Client-Anbieter für DB2.  
  
**Mode**  
Wählen Sie entweder Standard, TNSNAME oder Verbindungszeichenfolge-Modus.  
  
-   Im Modus "Standard" Geben Sie ein oder wählen Sie Werte für Anbieter, Servername, Server-Port, DB2-SID, Benutzername und Kennwort.  
  
-   Im Modus "TNSNAME" Geben Sie den Connect-Bezeichner (TNS Alias) von der DB2-Datenbank, Benutzernamen und das Kennwort ein.  
  
-   Im Modus "Verbindungszeichenfolge" Geben Sie eine Verbindungszeichenfolge an.  
  
    > [!IMPORTANT]  
    > Wir empfehlen nicht, dass Sie die Verbindungszeichenfolge-Modus verwenden, da der Text zum Beispiel Kennwörter sind, und sie wird als Klartext gesendet.  
  
Der Standardwert ist Modus "Standard".  
  
**Servername**  
Geben Sie den Namen des DB2-Servers ein. Der Standardservername ist identisch mit den Namen des Computers. Dies ist ein Modus "Standard"-Option.  
  
**Serverport**  
Wenn Sie eine Portnummer als 1521 (Standard) für Verbindungen mit DB2 verwenden, geben Sie die Portnummer ein. Dies ist ein Modus "Standard"-Option.  
  
**Verbinden Sie Bezeichner**  
Geben Sie ein DB2 connect-Bezeichner. Dies ist der Alias der Datenbank, wie in der Datei lokalen "TNSNames.ORA" definiert.  
  
Dies ist eine Option für TNSNAME Modus.  
  
**DB2 SID**  
Geben Sie die SID für die Datenbank ein. Die SID ist ein Bezeichner, der die DB2-Datenbank auf einem Computer unterscheidet. Der Standard-SID für eine Datenbank ist die ersten acht Zeichen des Datenbanknamens.  
  
Dies ist ein Modus "Standard"-Option.  
  
**Benutzername**  
Geben Sie den Benutzernamen ein, dem SSMA für die Verbindung mit der DB2-Datenbank verwendet werden.  
  
**Kennwort**  
Geben Sie das Kennwort für den Benutzernamen ein.  
  
**Verbindungszeichenfolge**  
> [!IMPORTANT]  
> Wir empfehlen nicht, dass Sie die Verbindungszeichenfolge-Modus verwenden, da der Text zum Beispiel Kennwörter sind, und sie wird als Klartext gesendet.  
  
Wenn Sie den Modus für die Verbindungszeichenfolge verwenden, geben Sie die vollständige Verbindungszeichenfolge für die Verbindung mit DB2.  
  
Verbindungszeichenfolgen werden von Name-Wert-Paaren bestehen.  
  
-   OLE DB-Verbindungszeichenfolgen finden Sie unter [Microsoft OLE DB-Anbieter für DB2](https://go.microsoft.com/fwlink/?LinkId=85640) Artikel in der MSDN Library.  
  
Für SSMA-Verbindungszeichenfolgen müssen Sie immer enthalten Sie die Provider-Parameter. Stellen Sie außerdem sicher, dass Sie den Port-Parameter enthalten, bei der Herstellung einer Verbindung mit DB2.  
  
