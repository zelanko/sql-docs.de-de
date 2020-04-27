---
title: Fehler- und Ereignisreferenz (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- messages [Reporting Services]
- errors [Reporting Services]
- Reporting Services, errors and events
- troubleshooting [Reporting Services], errors
- events [Reporting Services]
ms.assetid: 818b4cc1-e65d-4f1a-bf7d-fe269e6dd739
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2708c2609d23c6094cd69bddd08d958a85262d88
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099317"
---
# <a name="errors-and-events-reference-reporting-services"></a>Fehler- und Ereignisreferenz (Reporting Services)
  Dieses Thema enthält Informationen zu Fehlern und Ereignissen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Protokolldateien enthalten ebenfalls Fehlerinformationen. Weitere Informationen zu den verfügbaren Arten von Protokolldateien und zum Anzeigen der Protokolle finden Sie unter [Reporting Services-Protokolldateien und -Quellen](../report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="cause-and-resolution-for-reporting-services-error-messages"></a>Ursachen und Lösungen für Reporting Services-Fehlermeldungen  
 Für die häufig auf [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Websites gesuchten Fehlermeldungen sind Informationen zu Ursachen und Lösungen verfügbar. Weitere Informationen finden Sie unter [Cause and Resolution of Reporting Services Errors](cause-and-resolution-of-reporting-services-errors.md).  
  
## <a name="report-server-events"></a>Berichtsserverereignisse  
 Die folgenden Berichtsserverereignisse werden im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll aufgezeichnet.  
  
|Ereignis-ID|type|Category|`Source`|BESCHREIBUNG|  
|--------------|----------|--------------|------------|-----------------|  
|106|Fehler|Scheduling|Berichtsserver|Zum Definieren geplanter Operationen (beispielsweise Berichtsabonnierung und -übermittlung) muss SQL Server-Agent ausgeführt werden.|  
|[107](../../relational-databases/errors-events/mssqlserver-107-database-engine-error.md)|Fehler|Start/Herunterfahren|Berichtsserver<br /><br /> Prozessor für Zeitplanung und Übermittlung|*\<Quelle>* kann keine Verbindung mit der Berichtsserver-Datenbank herstellen. Weitere Informationen finden Sie unter [Report Server-Windows-Dienst &#40;MSSQLServer&#41; 107](../../relational-databases/errors-events/mssqlserver-107-database-engine-error.md).|  
|108|Fehler|Durchwahl|Berichtsserver<br /><br /> Berichts-Manager|*\<Quelle>* kann keine Übermittlungs-, Datenverarbeitungs- oder Renderingerweiterung laden.<br /><br /> Dies ist wahrscheinlich auf eine unvollständige Bereitstellung oder das Entfernen einer Erweiterung zurückzuführen. Weitere Informationen finden Sie unter [Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md) und [Deploying a Delivery Extension](../extensions/delivery-extension/deploying-a-delivery-extension.md).|  
|109|Information|Verwaltung|Berichtsserver<br /><br /> Berichts-Manager|Die Konfigurationsdatei wurde geändert. Weitere Informationen finden Sie unter [Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md).|  
|110|Warnung|Verwaltung|Berichtsserver<br /><br /> Berichts-Manager|Eine Einstellung in einer der Konfigurationsdateien wurde geändert und ist daher nicht mehr gültig. Stattdessen wird der Standardwert verwendet. Weitere Informationen finden Sie unter [Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md).|  
|111|Fehler|Protokollierung|Berichtsserver<br /><br /> Berichts-Manager|*\<Quelle>* kann das Ablaufverfolgungsprotokoll nicht erstellen. Weitere Informationen finden Sie unter [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).|  
|112|Warnung|Sicherheit|Berichtsserver|Der Berichtsserver hat einen möglichen Denial-of-Service-Angriff (DoS) entdeckt. Weitere Informationen finden Sie unter [Sicherheit und Schutz für Reporting Services](../security/reporting-services-security-and-protection.md).|  
|113|Fehler|Protokollierung|Berichtsserver|Der Berichtsserver kann einen Leistungsindikator nicht erstellen.|  
|114|Fehler|Start/Herunterfahren|Berichts-Manager|Der Berichts-Manager kann keine Verbindung mit dem Berichtsserverdienst herstellen.|  
|115|Warnung|Scheduling|Prozessor für Zeitplanung und Übermittlung|Eine geplante Aufgabe in der SQL Server-Agent-Warteschlange wurde geändert oder gelöscht.|  
|116|Fehler|Intern|Berichtsserver<br /><br /> Berichts-Manager<br /><br /> Prozessor für Zeitplanung und Übermittlung|Ein interner Fehler ist aufgetreten.|  
|117|Fehler|Start/Herunterfahren|Berichtsserver|Die Version der Berichtsserver-Datenbank ist ungültig.|  
|118|Warnung|Protokollierung|Berichtsserver<br /><br /> Berichts-Manager|Das Ablaufverfolgungsprotokoll befindet sich nicht an der erwarteten Verzeichnisposition. Ein neues Ablaufverfolgungsprotokoll wird im Standardverzeichnis erstellt. Weitere Informationen finden Sie unter [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).|  
|119|Fehler|Aktivierung|Berichtsserver<br /><br /> Prozessor für Zeitplanung und Übermittlung|*\<Quelle>* wurde kein Zugriff auf den Inhalt der Berichtsserver-Datenbank gewährt.|  
|120|Fehler|Aktivierung|Berichtsserver|Der symmetrische Schlüssel kann nicht entschlüsselt werden. Wahrscheinlichste Ursache ist eine Änderung des Kontos, unter dem der Dienst ausgeführt wird. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
|121|Fehler|Start/Herunterfahren|Berichtsserver|Fehler beim Starten des Remoteprozeduraufruf-Diensts.|  
|122|Warnung|Lieferung|Prozessor für Zeitplanung und Übermittlung|Der Prozessor für Zeitplanung und Übermittlung konnte keine Verbindung zum SMTP-Server herstellen, der für die Übermittlung von E-Mail verwendet wird. Weitere Informationen zu SMTP-Serververbindungen finden Sie unter [Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).|  
|123|Warnung|Protokollierung|Berichtsserver<br /><br /> Berichts-Manager|Der Berichtsserver konnte das Ablaufverfolgungsprotokoll nicht schreiben. Weitere Informationen zu Ablaufverfolgungsprotokollen finden Sie unter [Berichtsserverdienst-Ablaufverfolgungsprotokoll](../report-server/report-server-service-trace-log.md).|  
|124|Information|Aktivierung|Berichtsserver|Der Berichtsserverdienst wurde initialisiert. Weitere Informationen finden Sie unter [Initialisieren eines Berichtsservers (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-initialize-a-report-server.md).|  
|125|Information|Aktivierung|Berichtsserver|Der Schlüssel für die Datenverschlüsselung wurde erfolgreich extrahiert. Weitere Informationen zu Schlüsseln finden Sie unter [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
|126|Information|Aktivierung|Berichtsserver|Der Schlüssel für die Datenverschlüsselung wurde erfolgreich angewandt. Weitere Informationen zu Schlüsseln finden Sie unter [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
|127|Information|Aktivierung|Berichtsserver|Der verschlüsselte Inhalt wurde erfolgreich aus der Berichtsserver-Datenbank entfernt. Weitere Informationen zum Löschen von nicht wiederherstellbaren verschlüsselten Daten finden Sie unter [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
|128|Fehler|Aktivierung|Berichtsserver|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten aus verschiedenen Versionen können nicht zusammen verwendet werden.|  
|129|Fehler|Verwaltung|Berichtsserver<br /><br /> Prozessor für Zeitplanung und Übermittlung|Ein verschlüsselter Wert der Konfigurationseinstellung kann nicht entschlüsselt werden.|  
|130|Fehler|Verwaltung|Berichtsserver<br /><br /> Prozessor für Zeitplanung und Übermittlung|*\<Quelle>* kann die Konfigurationsdatei nicht finden. Konfigurationsdateien sind für den Berichtsserver erforderlich.|  
|131|Fehler|Sicherheit|Berichtsserver<br /><br /> Prozessor für Zeitplanung und Übermittlung|Ein verschlüsselter Benutzerdatenwert konnte nicht entschlüsselt werden.|  
|132|Fehler|Sicherheit|Berichtsserver|Fehler beim Verschlüsseln von Benutzerdaten. Der Wert kann nicht gespeichert werden.|  
|133|Fehler|Verwaltung|Berichtsserver<br /><br /> Berichts-Manager<br /><br /> Prozessor für Zeitplanung und Übermittlung|Fehler beim Laden der Konfigurationsdatei. Dieser Fehler kann auftreten, wenn XML ungültig ist.|  
|134|Fehler|Verwaltung|Berichtsserver|Der Berichtsserver konnte Werte für eine Einstellung in einer Konfigurationsdatei nicht verschlüsseln.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen Reporting Services Abonnements](../subscriptions/monitor-reporting-services-subscriptions.md)   
 [Reporting Services Log Files and Sources (Reporting Services-Protokolldateien und -Quellen)](../report-server/reporting-services-log-files-and-sources.md)  
  
  
