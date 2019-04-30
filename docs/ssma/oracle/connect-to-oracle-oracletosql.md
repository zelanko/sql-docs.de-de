---
title: Verbinden mit Oracle (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 23a48cb6-ff30-49bb-b4a7-603ebcab336f
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: da846d4afb4ce8fe745b98c8503901fe804520e0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63287724"
---
# <a name="connect-to-oracle-oracletosql"></a>Herstellen einer Verbindung mit Oracle (OracleToSQL)
Verwenden der **Herstellen einer Verbindung mit Oracle** im Dialogfeld Verbindung mit der Oracle-Datenbank, die Sie migrieren möchten.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit Oracle**. Wenn Sie zuvor eine Verbindung hergestellt haben, wird der Befehl ist **Wiederherstellen der Verbindung mit Oracle**.  
  
## <a name="options"></a>Optionen  
**Anbieter**  
Wählen Sie den Access-Datenanbieter für die Verbindung mit der Oracle-Datenbank. Verfügbare Anbieter werden die Oracle-Client-Anbieter und der OLE DB-Anbieter. Der Standardwert ist Oracle-Client-Anbieter.  
  
**Mode**  
Wählen Sie entweder Standard, TNSNAME oder Verbindungszeichenfolge-Modus.  
  
-   Im Modus "Standard" Geben Sie ein oder wählen Sie Werte für der Anbieter, Servername, ServerPort, Oracle SID, Benutzernamen und das Kennwort.  
  
-   Im Modus "TNSNAME" Geben Sie den Connect-Bezeichner (TNS Alias) von der Oracle-Datenbank, Benutzernamen und das Kennwort ein.  
  
-   Im Modus "Verbindungszeichenfolge" Geben Sie eine Verbindungszeichenfolge an.  
  
    > [!IMPORTANT]  
    > Wir empfehlen nicht, dass Sie die Verbindungszeichenfolge-Modus verwenden, da der Text zum Beispiel Kennwörter sind, und sie wird als Klartext gesendet.  
  
Der Standardwert ist Modus "Standard".  
  
**Servername**  
Geben Sie den Oracle-Servernamen ein. Der Standardservername ist identisch mit den Namen des Computers. Dies ist ein Modus "Standard"-Option.  
  
**Serverport**  
Wenn Sie eine Portnummer als 1521 (Standard) für Verbindungen mit Oracle verwenden, geben Sie die Portnummer ein. Dies ist ein Modus "Standard"-Option.  
  
**Verbinden Sie Bezeichner**  
Geben Sie die Oracle connect Bezeichner. Dies ist der Alias der Datenbank, wie in der Datei lokalen "TNSNames.ORA" definiert.  
  
Dies ist eine Option für TNSNAME Modus.  
  
**Oracle SID**  
Geben Sie die SID für die Datenbank ein. Die SID ist ein Bezeichner, der die Oracle-Datenbank auf einem Computer unterscheidet. Der Standard-SID für eine Datenbank ist die ersten acht Zeichen des Datenbanknamens.  
  
Dies ist ein Modus "Standard"-Option.  
  
**Benutzername**  
Geben Sie den Benutzernamen ein, dem SSMA für die Verbindung zur Oracle-Datenbank verwendet werden.  
  
**Kennwort**  
Geben Sie das Kennwort für den Benutzernamen ein.  
  
**Verbindungszeichenfolge**  
> [!IMPORTANT]  
> Wir empfehlen nicht, dass Sie die Verbindungszeichenfolge-Modus verwenden, da der Text zum Beispiel Kennwörter sind, und sie wird als Klartext gesendet.  
  
Wenn Sie den Modus für die Verbindungszeichenfolge verwenden, geben Sie die vollständige Verbindungszeichenfolge für die Verbindung zu Oracle.  
  
Verbindungszeichenfolgen werden von Name-Wert-Paaren bestehen.  
  
-   OLE DB-Verbindungszeichenfolgen finden Sie unter [Microsoft OLE DB-Anbieter für Oracle](https://go.microsoft.com/fwlink/?LinkId=85640) Artikel in der MSDN Library.  
  
Für SSMA-Verbindungszeichenfolgen müssen Sie immer enthalten Sie die Provider-Parameter. Stellen Sie außerdem sicher, dass Sie den Port-Parameter einschließen, wenn Sie eine Verbindung mit Oracle herstellen.  
  
