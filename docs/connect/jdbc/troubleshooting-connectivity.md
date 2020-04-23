---
title: Behandlung von Konnektivitätsproblemen
description: Erfahren Sie mehr über JDBC-Konnektivität und die Behandlung von möglichen Verbindungsproblemen bei Verwendung des Microsoft JDBC-Treibers für SQL Server.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bfba0b49-2e1f-411d-a625-d25fad9ea12d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: adb1203276e64f21f1834fc0ce0f0b5bb12a9321
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528334"
---
# <a name="troubleshooting-connectivity"></a>Behandlung von Konnektivitätsproblemen
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] setzt für die Kommunikation mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank voraus, dass TCP/IP installiert und aktiv ist. Sie können mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Configuration Manager überprüfen, welche Netzwerkbibliotheksprotokolle installiert sind.  
  
 Für Datenbankverbindungsfehler gibt es eine Vielzahl von Gründen, wie z. B.:  
  
-   TCP/IP ist für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht aktiviert, oder es wurde ein falscher Server oder eine falsche Portnummer angegeben. Überprüfen Sie, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an dem angegebenen Server und Port mit TCP/IP lauscht. In diesem Fall wird eine ähnliche Ausnahme wie die folgende gemeldet: "Fehler bei der Anmeldung. Es konnte keine TCP/IP-Verbindung zum Host hergestellt werden." die auf einen der folgenden Fehler hinweist:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist installiert, aber TCP/IP wurde nicht mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Netzwerkkonfiguration für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bzw. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Configuration Manager für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher als Netzwerkprotokoll für [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] installiert.  
  
    -   TCP/IP ist als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Protokoll installiert, lauscht aber nicht an dem in der JDBC-Verbindungs-URL angegebenen Port. Der Standardport ist 1433. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann aber bei der Produktinstallation für das Lauschen an einem beliebigen Port konfiguriert werden. Vergewissern Sie sich, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an Port 1433 lauscht. Sollte der Port geändert worden sein, vergewissern Sie sich, dass der in der JDBC-Verbindungs-URL angegebene Port dem geänderten Port entspricht. Weitere Informationen zu JDBC-Verbindungs-URLs finden Sie unter [Erstellen der Verbindungs-URL](../../connect/jdbc/building-the-connection-url.md).  
  
    -   Die Adresse des in der JDBC-Verbindungs-URL angegebenen Computers verweist nicht auf einen Server, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert und gestartet wurde.  
  
    -   Die TCP/IP-Netzwerkverbindung zwischen Client und dem Server mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funktioniert nicht. Sie können die TCP/IP-Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit Telnet überprüfen. Geben Sie dazu an der Eingabeaufforderung beispielsweise `telnet 192.168.0.0 1433` ein, wobei es sich bei 192.168.0.0 um die Adresse des Computers mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und bei 1433 um den Port handelt, an dem gelauscht wird. Wenn Sie eine Meldung erhalten, die darauf hinweist, dass keine Telnet-Verbindung möglich ist, lauscht TCP/IP nicht an dem entsprechenden Port auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindungen. Überprüfen Sie mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Netzwerkkonfiguration für [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] bzw. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Configuration Manager für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für den TCP/IP-Port 1433 konfiguriert ist.  
  
    -   Der vom Server verwendete Port wurde in der Firewall nicht geöffnet. Dazu gehört der Port, der vom Server verwendet wird, oder optional der Port, der einer benannten Instanz des Servers zugeordnet ist.  
  
-   Der angegebene Datenbankname ist falsch. Vergewissern Sie sich, dass Sie sich bei einer vorhandenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank anmelden.  
  
-   Der Benutzername oder das Kennwort ist falsch. Vergewissern Sie sich, dass die richtigen Werte verwendet werden.  
  
-   Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verwenden, setzt der JDBC-Treiber voraus, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung installiert ist. Dabei handelt es sich nicht um die Standardeinstellung. Vergewissern Sie sich beim Installieren oder Konfigurieren der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dass diese Option enthalten ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagnostizieren von Problemen mit dem JDBC-Treiber](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)   
 [Verbinden mit SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
