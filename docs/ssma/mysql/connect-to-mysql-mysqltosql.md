---
title: Verbinden mit MySQL (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 94099d01-ab19-4d58-a172-340c86b4a0f3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7289b3d5b287c1619a08921eba5cc30ff741e3b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63252708"
---
# <a name="connect-to-mysql-mysqltosql"></a>Herstellen einer Verbindung mit MySQL (MySqlToSql)
Verwenden der **Herstellen einer Verbindung mit MySQL** im Dialogfeld Verbindung mit der MySQL-Datenbank, die Sie migrieren möchten.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit MySQL**. Wenn Sie zuvor eine Verbindung hergestellt haben, wird der Befehl ist **Wiederherstellen der Verbindung mit MySQL**.  
  
## <a name="options"></a>Optionen  
**Anbieter**  
  
MySQL-Ressourcenanbieter verfügbar ist, MySQL 5.1 Odbcdriver (vertrauenswürdig).  
  
**Mode**  
  
Der Standardmodus ist Modus "Standard". Im Modus "Standard" Geben Sie ein oder wählen Sie Werte für die MySQL, Servername, Server-Port, Benutzername und Kennwort.  
  
**Servername**  
  
Geben Sie den MySQL-Servernamen ein. Dies ist ein Modus "Standard"-Option.  
  
**Serverport**  
  
Geben Sie den Server-Port. Der Server-Standardport ist 3306. Dies ist ein Modus "Standard"-Option.  
  
**Benutzername**  
  
Geben Sie den Benutzernamen ein, dem SSMA für die Verbindung mit der MySQL-Datenbank verwendet werden.  
  
**Kennwort**  
  
Geben Sie das Kennwort für den Benutzernamen ein.  
  
**SSL**  
  
Wenn Sie die sichere Verbindung mit MySQL herstellen möchten, verwenden von Secure Socket Layer (SSL) anhand der **SSL** Kontrollkästchen.  
  
**Konfigurieren**  
  
Es bietet eine Option aus, um die Verbindung mit MySQL über Secure Socket Layer (SSL) konfigurieren.  
  
> [!NOTE]  
> So aktivieren Sie **konfigurieren**, SSL muss festgelegt werden, um **"true"** .  
  
Wird Sie durch Klicken auf die Schaltfläche "Konfigurieren", ein Dialogfeld angezeigt. Definiert [Privacy Enhanced Mail-Zertifikate (PEM)], Verschlüsselung zu verwenden, beim Herstellen einer Verbindung mit MySQL-Datenbank, Pfad, an den folgenden drei Dateien, die in das Dialogfeld vorhanden sein muss:  
  
-   **SSL-Zertifizierungsstelle:** Gibt den Pfad zu einer Datei mit einer Liste von vertrauenswürdigen Zertifizierungsstellen mit SSL.  
  
-   **SSL-Zertifikat:** Gibt den Namen der Datei die SSL-Zertifikat zum Herstellen einer sicheren Verbindung verwendet.  
  
-   **SSL-SCHLÜSSEL:** Gibt den Namen der Schlüsseldatei SSL zum Herstellen einer sicheren Verbindung verwendet.  
  
> [!NOTE]  
> -   Die **OK** Schaltfläche ist aktiviert, wenn die erforderliche Informationen bereitgestellt wurde. Wenn die Dateipfade ungültig sind, bleiben die Schaltfläche "OK" deaktiviert.  
> -   Die **Abbrechen** Schaltfläche wird das Dialogfeld geschlossen und **deaktiviert** das Hauptformular der Verbindung die Option "SSL".  
  
