---
title: Herstellen einer Verbindung mit Sqlcmd | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sqlcmd
ms.assetid: 61a2ec0d-1bcb-4231-bea0-cff866c21463
caps.latest.revision: 45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c330fd329f28fa7d89b62b9af6bb8d4bb67c2bc4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38015804"
---
# <a name="connecting-with-sqlcmd"></a>Herstellen einer Verbindung mit sqlcmd
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Das [sqlcmd](http://go.microsoft.com/fwlink/?LinkID=154481)-Hilfsprogramm ist in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] unter Linux und macOS verfügbar.
  
Die folgenden Befehle demonstrieren, wie Sie mit der Windows-Authentifizierung (Kerberos) und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Authentifizierung bzw.:
  
```  
sqlcmd –E –Sxxx.xxx.xxx.xxx  
sqlcmd –Sxxx.xxx.xxx.xxx –Uxxx -Pxxx  
```  
  
## <a name="available-options"></a>Verfügbare Optionen

Im aktuellen Release sind die folgenden Optionen verfügbar:  
  
- -? Anzeige `sqlcmd` Nutzung.  
  
- -a Fordert eine Paketgröße an.  
  
- -b Beendet den Batchauftrag, wenn ein Fehler auftritt.  
  
- -C *Batch_terminator* Geben Sie das Batchabschlusszeichen.  
  
- -C Vertrauenswürdiges Serverzertifikat.  

- -d *Database_name* Problem eine `USE ` *Database_name* -Anweisung, wenn Sie starten `sqlcmd`.  

- -D Bewirkt, dass der Wert, der an die Option -S von `sqlcmd` übergeben wird, als Datenquellenname (Data Source Name, DSN) interpretiert wird. Weitere Informationen finden Sie unter „DSN-Unterstützung in `sqlcmd` und `bcp`“ am Ende dieses Themas.  
  
- -e Schreibt Eingabeskripts in das Standardausgabegerät (stdout).

- Verwenden Sie eine vertrauenswürdige Verbindung, integrierte Authentifizierung. Weitere Informationen zum vornehmen von vertrauenswürdiger Verbindungen, die die integrierte Authentifizierung von einem Client für Linux oder MacOS verwenden, finden Sie unter [Using Integrated Authentication](../../../connect/odbc/linux-mac/using-integrated-authentication.md).

- -h *number_of_rows* Gibt Sie die Anzahl der Zeilen an, die zwischen den Spaltenüberschriften ausgegeben werden sollen.  
  
- -H Gibt den Namen einer Arbeitsstation an.  
  
- -i *input_file*[,*input_file*[,…]] Identifiziert die Datei, die einen Batch mit SQL-Anweisungen oder gespeicherten Prozeduren enthält.  
  
- -Ich Satz der `SET QUOTED_IDENTIFIER` -Verbindungsoption auf ON.  
  
- -k Entfernt oder ersetzt Steuerzeichen.  
  
- **-K *** Application_intent*  
Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Der einzige derzeit unterstützte Wert ist **ReadOnly**. Wenn **-K** nicht angegeben wird, unterstützt `sqlcmd` keine Konnektivität mit einem sekundären Replikat in einer AlwaysOn-Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [ODBC-Treiber unter Linux und MacOS – hohe Verfügbarkeit und Notfallwiederherstellung](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
> [!NOTE]  
> **-K** wird in der CTP-Version für SUSE Linux nicht unterstützt. Sie können jedoch das Schlüsselwort **ApplicationIntent=ReadOnly** in einer DSN-Datei angeben, die an `sqlcmd` übergeben wird. Weitere Informationen finden Sie unter „DSN-Unterstützung in `sqlcmd` und `bcp`“ am Ende dieses Themas.  
  
- -l *Timeout* Geben Sie die Anzahl der Sekunden, bevor eine `sqlcmd` Login timeout, wenn Sie versuchen, die mit einem Server herstellen.

- -m *error_level* Steuert, welche Fehlernachrichten an stdout gesendet werden.  
  
- **-M *** Multisubnet_failover*  
Geben Sie immer **-M** an, wenn Sie eine Verbindung mit dem Verfügbarkeitsgruppenlistener einer [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]-Verfügbarkeitsgruppe oder einer [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]-Failoverclusterinstanz herstellen. **-M** gewährleistet eine schnellere Erkennung von Failovers und Verbindung mit dem (gerade) aktiven Server. Wenn **-M** nicht angegeben ist, ist **-M** deaktiviert. Weitere Informationen zu [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)], finden Sie unter [ODBC-Treiber unter Linux und MacOS – hohe Verfügbarkeit und Notfallwiederherstellung](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
> [!NOTE]  
> **-M** wird in der CTP-Version für SUSE Linux nicht unterstützt. Sie können jedoch das Schlüsselwort **MultiSubnetFailover=Yes** in einer DSN-Datei angeben, die an `sqlcmd` übergeben wird. Weitere Informationen finden Sie unter „DSN-Unterstützung in `sqlcmd` und `bcp`“ am Ende dieses Themas.  
  
- -N Verschlüsselt die Verbindung.  
  
- -o *output_file* Identifiziert die Datei, in welche die Ausgabe von `sqlcmd` geschrieben wird.  
  
- -p Gibt Leistungsstatistiken für jedes Resultset aus.  
  
- -P Gibt ein Benutzerkennwort an.  
  
- -Q *Commandline_query* Ausführen einer Abfrage bei `sqlcmd` wird gestartet, aber nicht beendet, wenn die Abfrage ausgeführt wurde.  

- -Q *Commandline_query* Ausführen einer Abfrage bei `sqlcmd` beginnt. `sqlcmd` wird beendet, wenn die Abfrage abgeschlossen ist.  

- -r Leitet die Fehlermeldungen an stderr um.

- -R Bewirkt, dass der Treiber die regionalen Einstellungen des Clients verwendet, um Währungs-, Datums- und Uhrzeitdaten in Zeichendaten zu konvertieren. Derzeit werden nur en_US-Formatierungen (US-Englisch) verwendet.
  
- -s *Column_separator_char* der Spaltentrennzeichen angeben.  

- -S [*protocol*:] *server*[**,***port*]  
Geben Sie die Instanz des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] herstellen oder wenn – D verwendet wird, einen DSN. Der ODBC-Treiber unter Linux und MacOS erfordert -S. Beachten Sie, dass **Tcp** ist das einzige gültige Protokoll.  
  
- -t *query_timeout* Gibt an, wie viele Sekunden verstreichen, bevor für einen Befehl (oder eine SQL-Anweisung) ein Timeout eintritt.  
  
- -u Gibt an, dass output_file unabhängig vom Format von input_file im Unicode-Format gespeichert wird.  
  
- -U *Login_id* Geben Sie eine Benutzeranmelde-ID.  
  
- -V *error_severity_level* Steuert den Schweregrad, der zur Festlegung der Variable ERRORLEVEL verwendet wird.  
  
- -w *Column_width* Geben Sie die Bildschirmbreite für die Ausgabe.  
  
- -W Entfernt nachfolgende Leerzeichen aus einer Spalte.  
  
- -x Deaktiviert die Variablenersetzung.  
  
- -X Deaktiviert Befehle, Startskripts und Umgebungsvariablen.  
  
- / y *Variable_length_type_display_width* legen Sie die `sqlcmd` Skriptvariable `SQLCMDMAXFIXEDTYPEWIDTH`.
  
- / Y *Fixed_length_type_display_width* legen Sie die `sqlcmd` Skriptvariable `SQLCMDMAXVARTYPEWIDTH`.


## <a name="available-commands"></a>Verfügbare Befehle

Im aktuellen Release sind die folgenden Befehle verfügbar:  
  
-   [:]!!  
  
-   :Connect  
  
-   :Error  
  
-   [:]EXIT  
  
-   GO [*count*]  
  
-   :Help  
  
-   :List  
  
-   :Listvar  
  
-   :On Error  
  
-   :Out  
  
-   :Perftrace  
  
-   [:]QUIT  
  
-   :r  
  
-   :RESET  
  
-   :setvar  
  
## <a name="unavailable-options"></a>Nicht verfügbare Optionen
Im aktuellen Release sind die folgenden Optionen nicht verfügbar:  

- -A Bewirkt die Anmeldung bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] über eine dedizierte Administratorverbindung (Dedicated Administrator Connection, DAC). Weitere Informationen zur Herstellung einer dedizierten Administratorverbindung (DAC) finden Sie unter [Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
- -f *code_page* Gibt die Eingabe- und Ausgabecodepages an.  
  
- -L Listet die lokal konfigurierten Servercomputer sowie die Namen der Servercomputer auf, die Broadcastnachrichten über das Netzwerk senden.  
  
- -v Erstellt eine `sqlcmd`-Skriptvariable, die in einem `sqlcmd`-Skript verwendet werden kann.  
  
Sie können die folgende alternative Methode verwenden: Schreiben Sie die Parameter in eine Datei, die Sie dann in eine andere Datei anfügen können. Dies hilft Ihnen dabei, eine Parameterdatei zu verwenden, um die Werte zu ersetzen. Erstellen Sie beispielsweise eine Datei namens `a.sql` (die Parameterdatei) mit dem folgenden Inhalt:
  
    :setvar ColumnName object_id  
    :setvar TableName sys.objects  
  
Erstellen Sie anschließend eine Datei namens `b.sql` mit den Parametern für den Ersatz:  
  
    select $(ColumnName) from $(TableName)  

Kombinieren Sie in der Befehlszeile `a.sql` und `b.sql` in `c.sql` mit den folgenden Befehlen:  
  
    cat a.sql > c.sql 
  
    cat b.sql >> c.sql  
  
Führen Sie `sqlcmd` und `c.sql` als Eingabedatei angegeben:  
  
    slqcmd -S<…> -P<..> –U<..> -I c.sql  

- -Z *Kennwort* Kennwort ändern.  
  
- -Z *Kennwort* Kennwort ändern und beenden.  

## <a name="unavailable-commands"></a>Nicht verfügbare Befehle

Im aktuellen Release sind die folgenden Befehle nicht verfügbar:  
  
-   :ED  
  
-   :ServerList  
  
-   :XML  
  
## <a name="dsn-support-in-sqlcmd-and-bcp"></a>DSN-Unterstützung in sqlcmd und bcp

Sie können bei der Option **sqlcmd** oder **bcp** `-S` (oder **sqlcmd**: Befehl verbinden) statt eines Servernamens einen Datenquellennamen (Data Source Name, DSN) angeben, wenn Sie -D angeben. -D bewirkt, dass **Sqlcmd** oder **Bcp** für die Verbindung mit dem Server, der im DSN angegeben ist, indem Sie die Option-s.  
  
System-DSNs werden gespeichert, der `odbc.ini` -Datei in die ODBC-SysConfigDir-Verzeichnis (`/etc/odbc.ini` auf standard-Installationen). Benutzer-DSNs werden in gespeichert `.odbc.ini` im Basisverzeichnis des Benutzers (`~/.odbc.ini`).
  
Die folgenden Einträge werden in einem DSN unter Linux oder macOS unterstützt:

-   **ApplicationIntent=ReadOnly**  

-   **Datenbank = *** Database_name*  
  
-   **Treiber = ODBC-Treiber 11 für SQLServer** oder **Treiber = ODBC-Treiber 13 für SQLServer**
  
-   **MultiSubnetFailover=Yes**  
  
-   **Server = *** Server_name_or_IP_address*  
  
-   **Trusted_Connection=yes**|**no**  
  
In einem DSN ist nur der Eintrag DRIVER erforderlich. Für die Verbindung mit einem Server benötigt `sqlcmd` oder `bcp` allerdings den Wert im Eintrag SERVER.  

Wenn diese Option sowohl im DSN als auch in der `sqlcmd`- oder `bcp`-Befehlszeile angegeben ist, überschreibt die Befehlszeilenoption den im DSN verwendeten Wert. Wenn der DSN z.B. einen DATABASE-Eintrag enthält und `sqlcmd`-Befehlszeile **-d** enthält, wird der an **-d** übergebene Wert verwendet. Wenn **Trusted_Connection=yes** im DSN angegeben ist, werden die Kerberos-Authentifizierung sowie der Benutzername (**–U**) verwendet und das Kennwort (**–P**), falls vorhanden, ignoriert.

Vorhandene Skripts, die `isql` aufrufen, können geändert werden, um `sqlcmd` zu verwenden, indem der folgende Alias definiert wird: `alias isql="sqlcmd –D"`.  

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Herstellen einer Verbindung mit **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md)  
 
