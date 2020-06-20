---
title: Ändern der Optionen für die Initialisierung von Momentaufnahmen für die SQL-Replikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 946d9035730512a626e710b1140a1ba01290908a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055634"
---
# <a name="modify-snapshot-initialization-options-for-sql-replication"></a>Ändern der Optionen für die Initialisierung von Momentaufnahmen für die SQL-Replikation

In diesem Artikel wird erläutert, wie eine Reihe von Optionen geändert werden, wenn [ein Abonnement mit einer Momentaufnahme initialisiert](initialize-a-subscription-with-a-snapshot.md)wird.

## <a name="snapshot-format"></a>Momentaufnahme Format
  Geben Sie das Momentaufnahme Format im Dialogfeld **Veröffentlichungs Eigenschaften- \<Publication> ** auf der Seite **Momentaufnahme** an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  

1.  Wählen Sie auf der Seite **Momentaufnahme** des Dialog Felds **Veröffentlichungs Eigenschaften- \<Publication> ** die Option System eigen **SQL Server-alle Abonnenten müssen Server mit SQL Server** oder Zeichen erforderlich sein, **Wenn ein Verleger oder Abonnent nicht SQL Server ausgeführt wird**. 

    > [!NOTE]  
    >  Sie sollten das systemeigene Format auswählen, sofern diese Veröffentlichung keine Abonnements für eine [!INCLUDE[ssEW](../../../includes/ssew-md.md)] -Datenbank und keine Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank unterstützen muss.    
1.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="snapshot-folder-locations"></a>Momentaufnahme Ordner Speicherorte

### <a name="default-snapshot-location"></a>Standardspeicherort für Momentaufnahmen
Geben Sie den standardmäßigen Momentaufnahme Speicherort (SQL Server Management Studio) den standardmäßigen Momentaufnahme Speicherort im Verteilungskonfigurations-Assistenten auf der Seite **Momentaufnahme Ordner** an. Weitere Informationen zum Verwenden dieses Assistenten finden Sie unter [Konfigurieren der Veröffentlichung und der Verteilung](configure-publishing-and-distribution.md). Wenn Sie eine Veröffentlichung auf einem Server erstellen, der nicht als Verteiler konfiguriert ist, geben Sie im Assistenten für neue Veröffentlichung auf der Seite **Momentaufnahmeordner** einen standardmäßigen Momentaufnahmespeicherort an. Weitere Informationen zum Zugreifen auf diesen Assistenten finden Sie unter [Erstellen einer Veröffentlichung](publish/create-a-publication.md).  
  
 Ändern Sie den standardmäßigen Momentaufnahme Speicherort auf der Seite **Verleger** des Dialog Felds **Verteiler Eigenschaften- \<Distributor> ** . Weitere Informationen finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md). Legen Sie den Momentaufnahme Ordner für die einzelnen Veröffentlichungen im Dialogfeld **Veröffentlichungs Eigenschaften- \<Publication> ** fest. Weitere Informationen finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
#### <a name="modify-the-default-snapshot-location"></a>Ändern des Standardspeicherorts für Momentaufnahmen  
  
1.  Klicken Sie im Dialogfeld **Verteiler Eigenschaften- \<Distributor> ** auf der Seite **Verleger** auf die Eigenschaften Schaltfläche (**...**) für den Verleger, dessen standardmäßiger Momentaufnahme Speicherort geändert werden soll.    
2.  Geben Sie im Dialogfeld **Verleger Eigenschaften- \<Publisher> ** einen Wert für die Eigenschaft **Standard Momentaufnahme Ordner** ein.

    > [!NOTE]  
    >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](security/secure-the-snapshot-folder.md).    
1.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

### <a name="alternate-snapshot-location"></a>Alternativer Snapshot-Speicherort
  Geben Sie im Dialogfeld **Veröffentlichungs Eigenschaften- \<Publication> ** auf der Seite **Momentaufnahme** einen alternativen Momentaufnahme Speicherort an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md). 

  
#### <a name="specify-an-alternate-snapshot-location"></a>Angeben eines alternativen Momentaufnahme Speicher Orts  
  
1.  Auf der Seite **Momentaufnahme** des Dialog Felds **Veröffentlichungs \<Publication> Eigenschaften-** :    
    1.  Aktivieren Sie **Dateien im folgenden Ordner speichern**, und klicken Sie dann auf **Durchsuchen** , um ein Verzeichnis auszuwählen, oder geben Sie den Pfad zu dem Verzeichnis ein, in dem Sie die Momentaufnahmedateien speichern möchten.    

        > [!NOTE]  
        >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](security/secure-the-snapshot-folder.md).    
    a.  Deaktivieren Sie **Dateien im Standardordner speichern** , es sei denn Momentaufnahmedateien müssen in beide Speicherorte geschrieben werden.    
     Zum Komprimieren von Momentaufnahmedateien aktivieren Sie **Momentaufnahmedateien in diesem Ordner komprimieren**. Die Komprimierung wird in der Regel für Verbindungen mit niedriger Bandbreite und für alternative Momentaufnahmespeicherorte auf Wechselmedien verwendet, z. B. einer CD-ROM.    
1.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]   


## <a name="compress-snapshot-files"></a>Komprimieren von Momentaufnahme Dateien
Geben Sie an, dass Dateien im Dialogfeld **Veröffentlichungs Eigenschaften- \<Publication> ** auf der Seite **Momentaufnahme** komprimiert werden sollen. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
1.  Auf der Seite **Momentaufnahme** des Dialog Felds **Veröffentlichungs \<Publication> Eigenschaften-** :  
  
    1.  Aktivieren Sie **Dateien im folgenden Ordner speichern**, und klicken Sie dann auf **Durchsuchen** , um ein Verzeichnis auszuwählen, oder geben Sie den Pfad zu dem Verzeichnis ein, in dem Sie die Momentaufnahmedateien speichern möchten.    
        > [!NOTE]  
        >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Sichern des Momentaufnahme Ordners](security/secure-the-snapshot-folder.md) .  
  
    2.  Deaktivieren Sie **Dateien im Standardordner speichern** , es sei denn Momentaufnahmedateien müssen in beide Speicherorte geschrieben werden.    
        > [!NOTE]  
        >  Wenn dieses Kontrollkästchen aktiviert ist, werden die im Standardordner gespeicherten Dateien nicht komprimiert. Komprimierte Dateien können nur im alternativen im vorigen Schritt angegebenen Speicherort gespeichert werden.    
2.  Wählen Sie **Momentaufnahmedateien in diesem Ordner komprimieren**aus.    
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="execute-scripts-before-and-after-snapshot-is-applied"></a>Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme

 Sie können angeben, ob Skripts auf dem Abonnenten vor oder nach dem Anwenden der Momentaufnahme ausgeführt werden. Skripts können für verschiedene Zwecke verwendet werden, z. B. zum Erstellen von Anmeldungen und Schemas (Objektbesitzer) auf den einzelnen Abonnenten.  
  
 Sie geben einen Dateispeicherort für jedes Skript an, und der Momentaufnahme-Agent kopiert jeweils bei der Verarbeitung der Momentaufnahme die Skriptdateien in den aktuellen Momentaufnahmeordner. Der Verteilungs-Agent oder der Merge-Agent führt das Vor-Momentaufnahme-Skript vor allen Skripts für replizierte Objekte aus, wenn eine Momentaufnahme angewendet wird. Der Verteilungs-Agent oder der Merge-Agent führt das Nach-Momentaufnahme-Skript nach der Momentaufnahme aus, nachdem alle anderen Skripts für replizierte Objekte und Daten angewendet wurden. Nachdem die Momentaufnahmeanwendung abgeschlossen ist und Skriptdateien erfolgreich ausgeführt wurden, werden die Skriptdateien aus dem Arbeitsverzeichnis auf dem Abonnenten entfernt.  
  
 Das Skript wird ausgeführt, indem das Hilfsprogramm **sqlcmd** gestartet wird. Führen Sie das Skript vor der Bereitstellung mithilfe von **sqlcmd** aus, um sicherzustellen, dass es erwartungsgemäß ausgeführt wird. Der Inhalt von Skripts, die vor und nach dem Anwenden der Momentaufnahme ausgeführt werden, muss wiederholbar sein. Wenn Sie z. B. eine Tabelle im Skript erstellen, müssen Sie zuerst ihr Vorhandensein überprüfen und daraufhin die entsprechende Aktion vornehmen. Das Skript muss wiederholbar sein, denn beim erneuten Initialisieren eines Abonnements, für das das Skript bereits angewendet wurde, wird das Skript erneut angewendet, wenn die neue Momentaufnahme während der erneuten Initialisierung angewendet wird.  
  
 Falls Sie die Momentaufnahmedatei komprimieren (indem sie in das CAB-Dateiformat von [!INCLUDE[msCoName](../../includes/msconame-md.md)] kopiert wird), werden die Skripts ebenfalls komprimiert und in der CAB-Datei platziert. Nachdem die komprimierte Momentaufnahmedatei zum Abonnenten übertragen und in ein Arbeitsverzeichnis auf dem Abonnenten dekomprimiert wurde, werden als Vor-Momentaufnahme-Skripts gekennzeichnete Skripts ausgeführt. Genauso werden alle Nach-Momentaufnahme-Skripts dekomprimiert und auf dem Abonnenten als letzter Schritt der Anwendung der Momentaufnahme ausgeführt.  

### <a name="execute-a-script-before-or-after-a-snapshot-is-applied"></a>Ausführen eines Skripts vor oder nach dem Anwenden einer Momentaufnahme  
 Geben Sie ein optionales Skript an, das vor oder nach dem Anwenden der Momentaufnahme im Dialogfeld **Veröffentlichungs Eigenschaften \<Publication> -** auf der Seite **Moment** Aufnahme ausgeführt werden soll. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  


1.  Auf der Seite **Momentaufnahme** des Dialog Felds **Veröffentlichungs \<Publication> Eigenschaften-** :    
    -   Wenn Sie ein Skript angeben möchten, das vor dem Anwenden der Momentaufnahme ausgeführt werden soll, klicken Sie auf **Durchsuchen** , um zum entsprechenden Skript zu navigieren, oder geben Sie im Textfeld **Dieses Skript vor Anwenden der Momentaufnahme ausführen** den Pfad zum gewünschten Skript ein. 
   
        > [!NOTE]  
        >  Der Verteilungs-Agent bzw. Merge-Agent muss für das von Ihnen angegebene Verzeichnis Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\computername\scripts\myscript.sql.    
    -   Wenn Sie ein Skript angeben möchten, das nach dem Anwenden der Momentaufnahme ausgeführt werden soll, klicken Sie auf **Durchsuchen** , um zum entsprechenden Skript zu navigieren, oder geben Sie im Textfeld **Dieses Skript nach Anwenden der Momentaufnahme ausführen** den UNC-Pfad zum gewünschten Skript ein.    
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
