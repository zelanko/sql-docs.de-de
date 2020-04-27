---
title: Datenbank-Engine Konfiguration-Konto Bereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 834b26bc-49de-4033-88d5-6aa7b1609720
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 300e3dd81ae7a3de2361c79864130c1361c19588
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095870"
---
# <a name="database-engine-configuration---account-provisioning"></a>Konfiguration der Datenbank-Engine - Kontobereitstellung
  Auf dieser Seite können Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsmodus festlegen und Windows-Benutzer oder -Gruppen als Administratoren von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]hinzufügen.  
  
## <a name="considerations-for-running-sscurrent"></a>Überlegungen für das Ausführen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wurde die Gruppe **BUILTIN\Administrators** für die Anmeldung bei [!INCLUDE[ssDE](../../includes/ssde-md.md)] bereitgestellt, und Mitglieder der lokalen Administratorgruppe konnten sich mit ihren Administratoranmeldeinformationen anmelden. Die Verwendung von erhöhten Berechtigungen ist keine bewährte Vorgehensweise. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wird die Gruppe **BUILTIN\Administrators** nicht für die Anmeldung bereitgestellt. Daher sollten Sie für jeden Administratorbenutzer eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung erstellen und diese während der Installation einer neuen Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]der festen Serverrolle sysadmin hinzufügen. Gehen Sie genauso für Windows-Konten vor, die zum Ausführen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträgen verwendet werden. Dies schließt auch Replikations-Agent-Aufträge ein.  
  
## <a name="options"></a>Optionen  
 **Sicherheitsmodus** – Wählen Sie Windows-Authentifizierung oder die Authentifizierung im gemischten Modus für die Installation aus.  
  
 **Windows-Prinzipal-Bereitstellung** – In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]befand sich die lokale Windows-Gruppe Vordefiniert\Administrator in der sysadmin-Serverrolle von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wodurch die Windows-Administratoren effektiv Zugriff auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz erhielten. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wird die Gruppe Vordefiniert\Administrator nicht in der Sysadmin-Serverrolle bereitgestellt. Stattdessen sollten Sie während des Setups explizit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administratoren für Neuinstallationen festlegen.  
  
> [!IMPORTANT]  
>  Sie müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administratoren für Neuinstallationen während des Setups explizit festlegen. Sie können den Setup-Vorgang erst nach Ausführung dieses Schrittes fortsetzen.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Administratoren angeben** – Sie müssen wenigstens einen Windows-Prinzipal für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angeben. Um das Konto hinzuzufügen, unter dem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup ausgeführt werden soll, klicken Sie auf die Schaltfläche **Aktueller Benutzer** . Um Konten zur Liste der Systemadministratoren hinzuzufügen bzw. daraus zu entfernen, klicken Sie auf **Hinzufügen** bzw. **Entfernen**, und bearbeiten Sie anschließend die Liste der Benutzer, Gruppen bzw. Computer, die Administratorrechte für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz haben sollen.  
  
 Wenn Sie die Bearbeitung der Liste abgeschlossen haben, klicken Sie auf **OK**, und überprüfen Sie anschließend die Liste der Administratoren im Konfigurationsdialogfeld. Sobald die Liste vollständig ist, klicken Sie auf **Weiter**.  
  
 Bei Auswahl des gemischten Authentifizierungsmodus müssen Sie Anmeldeinformationen für das vordefinierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemadministrator-(SA-)Konto angeben.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 **Windows-Authentifizierungsmodus**  
 Wenn ein Benutzer eine Verbindung über ein Windows-Benutzerkonto herstellt, überprüft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Kontonamen und Kennwort mithilfe des Tokens für den Windows-Prinzipal im Betriebssystem. Dieser als Standardauthentifizierungsmodus verwendete Modus bietet eine höhere Sicherheit als der gemischte Modus. Die Windows-Authentifizierung verwendet das Kerberos-Sicherheitsprotokoll, stellt Maßnahmen zur Durchsetzung von Kennwortrichtlinien, z. B. zur Überprüfung der Komplexität sicherer Kennwörter, bereit und bietet Unterstützung für Kontosperrungen und Ablauf von Kennwörtern.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Legen Sie auf keinen Fall ein leeres oder unsicheres sa-Kennwort fest.  
  
 **Gemischter Modus (Windows- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung oder-Authentifizierung)**  
 Ermöglicht Benutzern das Herstellen einer Verbindung mithilfe der Windows-Authentifizierung bzw. der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung. Benutzer, die mithilfe eines Windows-Benutzerkontos Verbindungen herstellen, können vertrauenswürdige Verbindungen verwenden, die von Windows überprüft werden.  
  
 Wenn Sie den gemischten Authentifizierungsmodus auswählen und beim Ausführen älterer Anwendungen ausschließlich SQL-Anmeldungen verwenden, müssen Sie für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konten sichere Kennwörter festlegen.  
  
> [!NOTE]  
>  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung wird nur aus Gründen der Abwärtskompatibilität bereitgestellt. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 **Kennwort eingeben**  
 Geben Sie die Systemadministratoranmeldung (sa) ein, uns bestätigen Sie sie. Kennwörter dienen als erste Schutzmaßnahme gegen Eindringlinge, daher ist die Festlegung sicherer Kennwörter von entscheidender Bedeutung für die Systemsicherheit. Legen Sie auf keinen Fall ein leeres oder unsicheres sa-Kennwort fest.  
  
> [!NOTE]  
>  Kennwörter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können zwischen 1 und 128 Zeichen (Kombinationen aus Buchstaben, Sonderzeichen und Ziffern) enthalten. Wenn Sie den gemischten Authentifizierungsmodus auswählen, müssen Sie ein sicheres sa-Kennwort eingeben, bevor Sie den Vorgang auf der nächsten Seite des Installations-Assistenten fortsetzen können.  
  
 **Richtlinien für sichere Kennwörter**  
 Sichere Kennwörter können von anderen nur schwer erraten und selbst von Computerprogrammen nicht ohne größeren Aufwand ausgespäht werden. Beim Festlegen von sicheren Kennwörtern dürfen keine verbotenen Richtlinien oder Bestimmungen verwendet werden, z. B.:  
  
-   Leeres Kennwort oder NULL  
  
-   Password  
  
-   "Admin"  
  
-   "Administrator"  
  
-   "sa"  
  
-   "sysadmin"  
  
 Beim Festlegen von sicheren Kennwörtern dürfen keine Angaben verwendet werden, die auf den Computer mit der Installation verweisen:  
  
-   Der Name des Benutzers, der zurzeit auf dem Computer angemeldet ist.  
  
-   Der Computername.  
  
 Ein sicheres Kennwort muss mehr als 8 Zeichen enthalten und wenigstens drei der folgenden vier Kriterien erfüllen:  
  
-   Es muss Großbuchstaben enthalten.  
  
-   Es muss Kleinbuchstaben enthalten.  
  
-   Es muss Zahlen enthalten.  
  
-   Es muss nicht alphanumerische Zeichen, z. B. #, % oder ^, enthalten.  
  
 Auf dieser Seite eingegebene Kennwörter müssen die Anforderungen der Richtlinien für sichere Kennwörter erfüllen. Bei Automatisierungen, die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden, sollten Sie sicherstellen, dass das Kennwort die Anforderungen der Richtlinien für sichere Kennwörter erfüllt.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Weitere Informationen zum Auswählen von Windows-Authentifizierung im Vergleich zu Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung finden Sie im Thema **Auswählen eines Authentifizierungsmodu** s in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 Weitere Informationen zur Auswahl eines Kontos für die Ausführung von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]finden Sie im Thema **Konfigurieren von Windows-Dienstkonten und -Berechtigungen** in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
