---
title: Konfigurieren von PolyBase-Konnektivität – Analytics Platform System | Microsoft-Dokumentation
description: Erläutert das Konfigurieren von PolyBase in Parallel Data Warehouse zur Verbindung mit externer Hadoop oder Microsoft Azure-BLOB-speicherdatenquellen. Verwenden Sie PolyBase zum Ausführen von Abfragen, die Daten aus mehreren Quellen, einschließlich Hadoop, Azure-BLOB-Speicher und Parallel Data Warehouse integrieren.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 26eeffb1d2a27ee49f01114b015ab4051b145d64
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909870"
---
# <a name="configure-polybase-connectivity-to-external-data"></a>Konfigurieren von PolyBase-Konnektivität für externe Daten
Erläutert das Konfigurieren von PolyBase in Parallel Data Warehouse zur Verbindung mit externer Hadoop oder Microsoft Azure-BLOB-speicherdatenquellen. Verwenden Sie PolyBase zum Ausführen von Abfragen, die Daten aus mehreren Quellen, einschließlich Hadoop, Azure-BLOB-Speicher und Parallel Data Warehouse integrieren.  
  
### <a name="to-configure-connectivity"></a>Zum Konfigurieren der Konnektivität  
  
1.  Öffnen Sie ein Abfragetool, z. B. Sqlcmd oder SQL Server Data Tools (SSDT), und führen Sie Sp_configure, um die aktuellen Einstellungen für "Hadoop Connectivity" anzuzeigen.  
  
    ![Hadoop-konnektivitätseinstellung](./media/configure-polybase-connectivity-to-external-data/APS_PDW_sp_configure.png "APS_PDW_sp_configure")  
  
2.  Entscheiden Sie, welche Hadoop-Konnektivität, die Einstellung muss und gibt an, ob Sie die aktuelle Einstellung ändern müssen. Diese Option gilt für die gesamte SQL Server-PDW-Region. Eine vollständige Liste der Konfigurationseinstellungen und Versionen, finden Sie unter [Sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
3.  Führen Sie zum Ändern der Einstellung 'Hadoop Connectivity' Sp_configure mit RECONFIGURE aus. Hier sind einige Beispiele.  
  
    ```sql  
    --Enable connectivity to Hortonworks Data Platform for Windows Server (HDP) or HDInsight’s Microsoft Azure blob storage  
    EXEC sp_configure 'hadoop connectivity', 4;   
    RECONFIGURE;  
  
    -- Enable connectivity to Hortonworks Data Platform (HDP)for Linux   
    EXEC sp_configure 'hadoop connectivity', 5;   
    RECONFIGURE;  
  
    -- Enable connectivity to Cloudera CDH for Linux   
    EXEC sp_configure 'hadoop connectivity', 3;   
    RECONFIGURE;  
  
    -- Disable the Hadoop connectivity option   
    EXEC sp_configure 'hadoop connectivity', 0;  
    RECONFIGURE;  
    ```  
  
    Ausgeführte Sp_configure mit RECONFIGURE legt den Konfigurationswert fest. Neustarten der Region ist erforderlich, zum Festlegen des Werts ausgeführt wird. Da ein Neustart erforderlich nach der nächste Stopp auch ist, müssen Sie nicht den Neustart, bis Sie nach dem nächsten Schritt werden die "Core-Site.xml" ändert.  
  
4.  Um Microsoft Azure-Blob-Speicher als eine externe Datenquelle zu aktivieren, fügen Sie eine oder mehrere Microsoft Azure Speicherkonto-Zugriffsschlüssel zu PDW-Core-site.xml-Datei ein. So fügen Sie einen Schlüssel hinzu:  
  
    1.  Suchen Sie Ihr Microsoft Azure Storage-Kontoname. Zum Anzeigen Ihrer Speicherkonten, melden Sie sich die[Azure-Portal](https://portal.azure.com) , und klicken Sie auf **Speicherkonten (klassisch)**.  
  
        ![Windows Azure Storage-Kontoname](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountName.png "APS_PDW_AzureStorageAccountName")  
  
    2.  Suchen Sie Ihre Azure-Speicherkonto-Zugriffsschlüssel. Zu diesem Zweck klicken Sie auf den Namen Ihres Speicherkontos, und klicken Sie auf dem Blatt "Einstellungen" auf **Schlüssel**. Dies zeigt Ihnen, Ihre Namen und den kontoschlüssel.  
  
        ![Windows Azure-speicherzugriffsschlüsseln](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountAccessKey.png "APS_PDW_AzureStorageAccountAccessKey")  
  
    3.  Öffnen Sie eine Remotedesktopverbindung mit dem Steuerungsknoten mit PDW.  
  
    4.  Öffnen Sie die Datei c:\Programme\Microsoft c:\Programme\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\core-site.xml.  
  
    5.  Fügen Sie die folgende Eigenschaft mit den Attributen Name und Wert hinzu, um "Core-Site.xml".  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.<your storage account name>.blob.core.windows.net</name>  
          <value><your storage account access key></value>  
        </property>  
        ```  
  
        Dieses Beispiel verwendet den Namen und den kontoschlüssel beschrieben.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.CustomerX.blob.core.windows.net</name>  
          <value>yyeTfCxxxxxxxxQ5WdnapXw77W+FwzHUhX/p/f26fIpnNFGtewzyRN90e1/qmTOl1xxxxxxxxa0goG71LsNcw==</value>  
        </property>  
        ```  
  
        > [!CAUTION]  
        > Nehmen Sie Sicherheitsmaßnahmen vor dem Speichern des Zugriffsschlüssels in "Core-Site.xml" aus. Jeder Benutzer mit CONTROL SERVER oder ALTER ANY EXTERNAL DATA SOURCE-Berechtigung kann eine externe Datenquelle erstellen, die auf dieses Konto zugreift. Sobald die externe Datenquelle erstellt wurde, können alle SQL Server-PDW-Benutzer mit CREATE TABLE-Berechtigungen auf eine externe Tabelle erstellen, die dieses Speicherkonto greift auf. Die Benutzer können dann Konto den Datenzugriff und nutzen Ressourcen im Konto.  
  
    6.  Speichern der Änderungen in "Core-Site.xml".  
  
5.  Yarn.application.classpath-Eigenschaft und die Werte der Yarn-site.xml-Datei hinzufügen.  
  
    Überspringen Sie diesen Schritt, wenn Sie mit einer externen Hadoop-1.3 verbinden.  
  
    Ab Hadoop 2.0, enthält die Datei "Yarn-Site.xml" Konfigurationseinstellungen für Hadoop YARN-Framework. Diese Datei befindet sich auf dem steuerknoten unter **C:\program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\\**.  
  
    Um PolyBase-Abfragen mit einem externen Hadoop-2.0-Cluster unter Windows oder Linux ausführen zu können, müssen Sie die yarn.application.classpath-Eigenschaft und die Werte, die konsistent mit den Einstellungen "Yarn-Site.xml" auf dem externen Hadoop-Cluster zu konfigurieren. Diese Konfiguration ist erforderlich, selbst wenn Ihre externen Hadoop-Cluster die Standardeinstellungen verwendet.  
  
    Beispiel für Standard-Einstellungen:  
  
    ```xml  
    <property>  
        <name>yarn.application.classpath</name>  
        <value>  
          %HADOOP_CONF_DIR%,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/*,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/lib/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/lib/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/lib/*  
         </value>  
      </property>  
    ```  
  
    Sobald eine beliebige Eigenschaft in "Yarn-Site.xml" definiert ist, verwendet PolyBase die eigenschafteneinstellungen, bei der Ausführung von Abfragen für Hadoop. Wenn PolyBase-Abfragen für sowohl für Azure Storage-Blob als auch für einen externen Hadoop-2.0-Cluster in Windows ausgeführt werden sollen, muss für alle Dateien "Yarn-Site.xml" Konsistenz vorhanden sein. Andernfalls schlägt fehl, die PolyBase-Abfragen.  
   
6.  Starten Sie die PDW-Region neu. Zu diesem Zweck verwenden Sie das Configuration Manager-Tool. Finden Sie unter [Starten des Konfigurations-Managers &#40;Analytics-Plattformsystem&#41;](launch-the-configuration-manager.md).  
  
7.  Überprüfen Sie die Sicherheitseinstellungen für Hadoop-Verbindungen. Wenn die **schwache Authentifizierung** auf Hadoop Seite aktiviert ist, mithilfe von `dfs.permission = true`, müssen Sie einen Hadoop-Benutzer erstellen **Pdw_user** und gewähren von vollständigen Lese- und Schreibberechtigungen für diesen Benutzer. SQL Server PDW und den entsprechenden Aufrufen der von SQL Server PDW werden immer als ausgegeben **Pdw_user**.  Dies ist ein fester Benutzername und kann nicht in dieser Version von Hadoop-Konnektivität und SQL Server-PDW-Release geändert werden. Wenn Sicherheit in Hadoop deaktiviert ist, mithilfe von `dfs.permission = false`, und klicken Sie dann keine weiteren Aktionen ausgeführt werden müssen.  
  
8.  Entscheiden Sie, welche Benutzer auf eine externe Datenquelle in der Microsoft Azure Blob Storage erstellen können. Geben Sie jedem dieser Benutzer den Namen des Speicherkontos sowie **ALTER ANY EXTERNAL DATA SOURCE** oder **CONTROL SERVER** Berechtigung.  
  
9. Entscheiden Sie für Hadoop-Verbindungen, welche Benutzer auf eine externe Datenquelle mit Hadoop in Azure erstellen können. Geben Sie jedem Benutzer die IP-Adresse und Port die Anzahl der einzelnen Hadoop-namenode an, und geben sie **ALTER ANY EXTERNAL DATA SOURCE** oder **CONTROL SERVER** Berechtigung.  
  
10. Herstellen einer Verbindung mit dem WASB erfordert auch die DNS-Weiterleitung auf dem Gerät konfiguriert werden. Um die DNS-Weiterleitung konfigurieren zu können, finden Sie unter [verwenden Sie eine DNS-Weiterleitung zum Auflösen nicht zu Appliances DNS-Namen &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
Autorisierte Benutzer können jetzt Daten aus externen Quellen und externe Dateiformate, externe Tabellen erstellen. Sie können diese verwenden, um Daten aus mehreren Quellen einschließlich Hadoop, integrieren, die Microsoft Azure Blob Storage und SQL Server PDW.  

## <a name="kerberos-configuration"></a>Kerberos-Konfiguration  
Beachten Sie, dass wenn PolyBase bei einem gesicherten Cluster von Kerberos authentifiziert wird, muss die Einstellung "Hadoop.RPC.Protection" auf die Authentifizierung festgelegt werden. Dadurch bleibt die Datenkommunikation zwischen den Hadoop-Knoten unverschlüsselt. 

 Die Verbindung mit einem Kerberos-gesicherte Hadoop-Cluster [mithilfe von MIT KDC]:
   
  
1.  Suchen Sie die Hadoop-Konfigurationsverzeichnis im Installationspfad auf dem steuerknoten:  
  
    ```  
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```  
  
2.  Suchen Sie den hadoopseitigen Konfigurationswert der in dieser Tabelle aufgelisteten Konfigurationsschlüssel. (Suchen Sie die Dateien auf dem Hadoop-Computer im Hadoop-Konfigurationsverzeichnis.)  
  
3.  Kopieren Sie die Konfigurationswerte in der Value-Eigenschaft in den entsprechenden Dateien auf dem steuerknoten an.  
  
    |**#**|**Konfigurationsdatei**|**Konfigurationsschlüssel**|**Aktion**|  
    |------------|----------------|---------------------|----------|   
    |1|core-site.xml|polybase.kerberos.kdchost|Geben Sie den KDC-Hostnamen an. Zum Beispiel: kerberos.ihr-bereich.de.|  
    |2|core-site.xml|polybase.kerberos.realm|Geben Sie den Kerberos-Bereich an. Zum Beispiel: IHR-BEREICH.DE|  
    |3|core-site.xml|hadoop.security.authentication|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: KERBEROS<br></br>**Sicherheitshinweis:** KERBEROS muss in Großbuchstaben geschrieben werden. Bei Kleinschreibung ist die Funktionalität nicht gewährleistet.|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: hdfs/_HOST@YOUR-REALM.COM|  
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: mapred/_HOST@YOUR-REALM.COM|  
    |6|mapred-site.xml|mapreduce.jobhistory.address|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Zum Beispiel: 10.193.26.174:10020|  
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Suchen Sie die hadoopseitige Konfiguration, und kopieren Sie diese auf den SQL Server-Computer. Beispiel: yarn/_HOST@YOUR-REALM.COM|  
  
4. Erstellen Sie ein datenbankweites Anmeldeinformationsobjekt, um die Authentifizierungsinformationen für jeden Hadoop-Benutzer anzugeben. Weitere Informationen finden Sie unter [PolyBase T-SQL-Objekte](../relational-databases/polybase/polybase-t-sql-objects.md).  

5. Starten Sie die PDW-Region neu. Zu diesem Zweck verwenden Sie das Configuration Manager-Tool. Finden Sie unter [Starten des Konfigurations-Managers &#40;Analytics-Plattformsystem&#41;](launch-the-configuration-manager.md).
 
## <a name="see-also"></a>Siehe auch  
[Konfiguration von Sicherheitsgeräten &#40;Analytics Platform System&#41;](appliance-configuration.md)  
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
