---
title: Problembehandlung für Big Data-Cluster (BDC) mit Jupyter-Notebooks und Azure Data Studio
titleSuffix: SQL Server Big Data Clusters
description: Problembehandlung für BDC mit Jupyter-Notebooks und Azure Data Studio in einem SQL Server 2019 Big Data-Cluster.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 09/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 073776c042c0a0da136347c8e1658603b755208f
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92378405"
---
# <a name="troubleshooting-big-data-clusters-bdc-with-notebooks"></a>Problembehandlung für Big Data-Cluster (BDC) mit Notebooks

Diese Seite ist ein Index der Notebooks für SQL Server-Big Data-Cluster. Dieses ausführbaren Notebooks (IPYNB) sind für SQL Server 2019 entwickelt, um bei der Problembehandlung von Big Data-Clustern zu helfen.

Jedes Notebook überprüft seine eigenen Abhängigkeiten. Die Ausführung von **run all cells** (Alle Zellen ausführen) wird entweder erfolgreich abgeschlossen oder löst eine Ausnahme aus, die einen Hinweis mit einem Link zu einem anderen Notebook enthält, um die fehlende Abhängigkeit aufzulösen. Folgen Sie dem Link im Hinweis zu dem folgenden Notebook, klicken Sie auf **run all cells** , und wenn die Aktion erfolgreich ist, kehren Sie zum ursprünglichen Notebook zurück, und führen Sie **run all cells** aus.

Wenn alle Abhängigkeiten installiert wurden, **run all cells** aber fehlschlägt, analysiert jedes Notebook die Ergebnisse und erzeugt, wo möglich, einen Hinweis mit Link zu einem weiteren Notebook, um bei der weitergehenden Behandlung des Problems zu helfen.


## <a name="troubleshooting-big-data-cluster-bdc"></a>Problembehandlung für einen Big Data-Cluster (BDC)

Dieser Abschnitt enthält eine Reihe von Notebooks, mit denen Protokolle aus einem SQL Server-Big Data-Cluster (BDC) abgerufen werden können.

|Name |Beschreibung |
|---|---|---|---|
|TSG100: Problembehandlung für Big-Data-Cluster|Übersicht über alle verfügbaren Notebooks, mit denen sich BDC-Probleme (Big Data Cluster) beheben lassen, und Informationen dazu, wann sie zu verwenden sind  |
|TSG101 – Problembehandlung in SQL Server|Übersicht über alle verfügbaren Notebooks, mit denen sich SQL Server-Probleme beheben lassen, und Informationen dazu, wann sie zu verwenden sind  |
|TSG102 – Problembehandlung im HDFS|Übersicht über alle verfügbaren Notebooks, mit denen sich HDFS-Probleme beheben lassen, und Informationen dazu, wann sie zu verwenden sind  |
|TSG103 –Spark-Problembehandlung|Übersicht über alle verfügbaren Notebooks, mit denen sich Spark-Probleme beheben lassen, und Informationen dazu, wann sie zu verwenden sind  |
|TSG104 – Kontrolle der Problembehandlung|Übersicht über alle verfügbaren Notebooks, mit denen sich Controllerprobleme beheben lassen, und Informationen dazu, wann sie zu verwenden sind  |
|TSG105 – Gatewayproblembehandlung|Übersicht über alle verfügbaren Notebooks, mit denen sich Knox-Gateway-Probleme beheben lassen, und Informationen dazu, wann sie zu verwenden sind  |
|TSG106 – App-Problembehandlung|Übersicht über alle verfügbaren Notebooks, mit denen sich App-Bereitstellungsprobleme (App-Deploy-Probleme) beheben lassen, und Informationen dazu, wann sie zu verwenden sind  |



## <a name="diagnose-issues-from-big-data-clusters-bdc"></a>Diagnostizieren von Problemen aus Big Data-Clustern (BDC)

Eine Reihe von Notebooks zur Diagnose von Szenarios und Zuständen mit einem Big-Data-Cluster.

|Name |Beschreibung |
|---|---|---|---|
|TSG002 – CrashLoopBackoff|Mit diesem TSG wird eine Verbindung mit jedem Container hergestellt, dessen letzter Versuch, in den Status „Wird ausgeführt“ (Running) zu gelangen, fehlgeschlagen ist, und werden das aktuelle und das vorherige Containerprotokoll abgerufen. Dies ist nützlich zum Debuggen von CrashLoopBackOff-Problemen, die in „kubectl get pods“ gemeldet werden.|
|TSG025 – FSM-Browser – FSM-Controllerzustand abfragen|Verwenden Sie dieses Notebook, um eine Verbindung mit der Controller-Datenbank herzustellen und den Status des finiten Zustandscomputers (FSM) zu durchsuchen. Verwenden Sie dieses Notebook, um aktive Zustandscomputer aufzulisten und hängengebliebene Workflows zu identifizieren.|
|TSG026 – Mit dem Datenpoolknoten verbinden (zum Ausführen von T-SQL)|Verwenden Sie dieses Notebook, um eine Verbindung mit dem Datenpoolknoten herzustellen (zum Ausführen von T-SQL).|
|TSG027 – Clusterbereitstellung beobachten|Verwenden Sie dieses Notebook, um eine Clusterbereitstellung zu beobachten. Das Notebook bietet Anleitung zum Beheben von Problemen bei der Big-Data-Clustererstellung in SQL Server, wobei die folgenden Befehle häufig nützlich sind, um die Ursachen zu ermitteln. |
|TSG029 – Sicherungen im Cluster suchen|Verwenden Sie dieses Notebook, um nach Coredumps und Minidumps aus Prozessen wie SQL Server oder Controller in einem Big-Data-Cluster zu suchen.|
|TSG032 – CPU- und Arbeitsspeicherauslastung für alle Container|Verwenden Sie dieses Notebook, um CPU- und Arbeitsspeicherauslastung für alle Container zu überprüfen.|
|TSG037 – Masterpoolpod bestimmen, der das primäre Replikat hostet|Verwenden Sie dieses Notebook, um den Masterpoolpod zu bestimmen, der das primäre Replikat für den Big Data-Cluster hostet, wenn die Masterpool-Hochverfügbarkeit aktiviert ist.|
|TSG044 – sqlcmd im Masterpoolcontainer ausführen|Verwenden Sie dieses Notebook, um direkt eine Verbindung mit einem Masterpoolknoten über T-SQL herzustellen.|
|TSG055 – Zeit zwischen Curl und Sparkhead|Verwenden Sie dieses Notebook, um einen Schritt zu diagnostizieren und zu ermitteln, wie lang die Curl-Antwortzeit vom Controllerpod zum Sparkhead-Pod ist.|
|TSG060 – Persistenter Speicherplatz auf dem Volumedatenträger für alle Big-Data-Cluster-PVCs|Verwenden Sie dieses Notebook, um eine Verbindung mit jedem Container herzustellen und den Speicherplatz abzurufen, der für das beständige Volume (Persisted Volume, PV) verwendet wird bzw. verfügbar ist, das jedem beständigen Volumeanspruch (Persisted Volume Claim, PVC) eines Big-Data-Clusters (BDC) zugeordnet ist.|
|TSG078 – Funktioniert der Cluster fehlerfrei?|Verwenden Sie dieses Notebook, um zu überprüfen, ob ein Big Data-Cluster (BDC) fehlerfrei ist.|
|TSG079 – Kernspeicherabbild für Controller erstellen|Verwenden Sie dieses Notebook, um ein Kernspeicherabbild für einen Controller zu erstellen.|
|TSG086 – In allen Containern zuerst ausführen|Verwenden Sie dieses Notebook, um dies in allen Containern zuerst auszuführen.|
|TSG087 – hadoop fs-CLI im namenode-Pod verwenden|Verwenden Sie dieses Notebook, um hadoop fs-CLI im namenode-Pod zu verwenden.|
|TSG108 – Konfigurationszurodnung für Controllerupgrade anzeigen|Verwenden Sie dieses Notebook, um den Fehler zu beheben, wenn Sie ein Big Data-Cluster-Upgrade mit **azdata bdc upgrade** ausführen.|
|TSG112 – Prüfungen vor Active Directory-Bereitstellung|Verwenden Sie dieses Notebook, um zu überprüfen, ob eine Big Data-Cluster-Konfiguration (BDC) für eine Active Directory-Bereitstellung (AD) gültig ist.|
|TSG115 – Übersetzer für SQL Server für Linux-Sicherheitsprotokolle|Verwenden Sie dieses Notebook, um die Protokolle zu analysieren, die von der „security.ldap“- und der „security.kerberos“-Protokollierung für SQL Server für Linux erstellt wurden. Um diese Protokollierungen zu aktivieren, platzieren Sie die folgenden Zeilen in „/var/opt/mssql/logger.ini“ auf dem Computer, auf dem SQL Server für Linux ausgeführt wird. Hinweis: Für diese Datei wird zwischen Groß- und Kleinschreibung unterschieden.|
|TSG116 – Übersetzer für SQL BDC-Sicherheitsunterstützungsprotokoll|Verwenden Sie dieses Notebook, um die Protokolle zu analysieren, die vom Sicherheitsunterstützungsdienst (Security Support Service) in SQL BDC erstellt wurden. Um die Protokolle zu erstellen, werden die Debugprotokolle aus dem Cluster kopiert und extrahiert. Führen Sie die folgenden Schritte aus: – Führen Sie „azdata bdc debug copy-logs -n <namespace> *“ aus. Dadurch werden mehrere „.tar.gz“-Dateien erstellt. – Extrahieren Sie den Inhalt von „debuglogs-* <namespace>-<date>-<time>.tar.gz“. – Suchen Sie nach dem Sicherheitsunterstützungsprotokoll, das in „./<namespace>/control-<…>/security-support/supervisol/log/secsupp-stderr---<…>.log.“ gespeichert ist.|
|TSG119 – Prüfungen nach Active Directory-Bereitstellung|Dieses Notebook ist dafür vorgesehen, eine BDC-Konfiguration nach einer AD-Bereitstellung zu überprüfen. Es überprüft das Vorhandensein von DNS-Einträgen für alle Endpunkte mit einem dnsName-Attribut, und diese DNS-Einträge sollten Hosteinträge, keine Aliase (d. h. A-Einträge, nicht CNAME-Einträge) sein. Außerdem wird das Vorhandensein von bekannten AD-Konten und ob sie aktiviert sind oder nicht und das Vorhandensein der erwarteten SPNs überprüft.|






## <a name="repair-issues-from-big-data-clusters-bdc"></a>Beheben von Problemen aus Big Data-Clustern (BDC)

Eine Reihe von Notebooks zum Beheben bekannter Probleme und Zustände eines SQL Server-Big-Data-Clusters.

|Name |Beschreibung |
|---|---|---|---|
|TSG005: „Forwarding loop detected“ (Weiterleitungsschleife erkannt)|Verwenden Sie dieses Notebook, um das Problem „Weiterleitungsschleife erkannt“ zu verarbeiten. Das Hilfsprogramm dnsmasq kann eine lokale Loopbackadresse in „resolv.conf“ eintragen, was dazu führen kann, dass die Controllerpods während der ersten Clusterbereitstellung in den CrashLoopBackOff-Zustand versetzt werden: https://askubuntu.com/questions/627899/nameserver-127-0-1-1-in-resolv-conf-wont-go-away|
|TSG011 – sparkhistory-Server neu starten|Verwenden Sie dieses Notebook, um den sparkhistory-Server neu zu starten, weil sich der sparkhistory-Java-Prozess während des Starts aufhängen kann. Durch Neustarten des sparkhistory-Servers (supervisorctl restart sparkhistory) kann dieses Problem behoben werden.|
|TSG018: Beenden des sqlservr-Prozesses im Masterpool| Verwenden Sie dieses Notebook, wenn T-SQL SHUTDOWN den ./sqlservr-Prozess nicht erfolgreich wiederherstellen kann. Verwenden Sie dieses Notebook, um den sqlservr-Hauptprozess zu beenden, der durch den ./sqlservr-Front-End-Prozess automatisch neu gestartet wird.|
|TSG024: Namenode befindet sich im abgesicherten Modus| Verwenden Sie dieses Notebook, wenn sich HDFS selbst in den abgesicherten Modus schaltet. Wenn z. B. zu viele Pods im Speicherpool zu schnell neu gestartet werden, kann es sein, dass der abgesicherte Modus automatisch aktiviert wird.|
|TSG028 – Knoten-Manager auf allen Speicherpoolknoten neu starten| Verwenden Sie dieses Notebook, wenn der Knoten-Manager auf allen Speicherpoolknoten neu gestartet werden muss.|
|TSG038 – Fehler bei der BDC-Erstellung, weil der –doc-Schlüssel fehlt| Verwenden Sie dieses Notebook, wenn BDC-Erstellung wegen „Schlüssel für Dok. fehlt“ fehlschlägt.|
|TSG039 – Ungültiger Objektname „role_permissions“| Verwenden Sie dieses Notebook, wenn ein „ungültiges Objekt“-Problem aufgrund der Rollenberechtigung in Knox „gateway.log“ vorliegt.|
|TSG040: „Failed to get file names from controller with Error“ (Die Dateinamen konnten nicht vom Controller abgerufen werden. Der folgende Fehler ist aufgetreten: …)| Verwenden Sie dieses Notebook, wenn ein 504-Gatewaytimeout auftritt, während Dateinamen vom Controller abgerufen werden.|
|TSG041 – Es konnte kein neuer asynchroner E/A-Kontext erstellt werden (erhöhen Sie sysctl fs.aio-max-nr)| Verwenden Sie dieses Notebook, wenn es nicht möglich ist, einen neuen asynchronen E/A-Kontext zu erstellen (erhöhen Sie sysctl fs.aio-max-nr).|
|TSG045 – die maximale Anzahl von Datenträgern, die an eine VM dieser Größe angefügt werden dürfen (AKS)| Verwenden Sie dieses Notebook, wenn Sie die maximale Anzahl von Datenträgern ermitteln möchten, die an eine VM dieser Größe angefügt werden dürfen (AKS).|
|TSG047: ConfigException – „Expected only one object with name“ (Nur ein Objekt mit dem Namen … wurde erwartet)| Verwenden Sie dieses Notebook, wenn eine Konfigurationsausnahme (ConfigException) vorliegt, bei der nur ein Objekt mit dem Namen erwartet wird.|
|TSG048 – Bereitstellung hängt bei „Waiting for controller pod to be up“ (Warten, bis der Controllerpod eingerichtet ist).| Verwenden Sie dieses Notebook, wenn die Bereitstellung bei „Waiting for controller pod to be up“ (Warten, bis der Controllerpod eingerichtet ist) hängt.|
|TSG050: Während der Clustererstellung kommt es zu einem Absturz, und der Fehler „timeout expired waiting for volumes to attach or mount for pod“ (Beim Anfügen oder Einbinden von Volumes für den Pod … ist eine Zeitüberschreitung aufgetreten) tritt auf| Verwenden Sie dieses Notebook, wenn es während der Clustererstellung zu einem Absturz kommt, und der Fehler „timeout expired waiting for volumes to attach or mount for pod“ (Beim Anfügen oder Einbinden von Volumes für den Pod … ist eine Zeitüberschreitung aufgetreten) auftritt.|
|TSG052 – Fehler beim Abrufen des master-svc-DNS, es wird ein neuer Versuch unternommen| Verwenden Sie dieses Notebook, wenn es während der Clustererstellung zu einem Absturz kommt, und der Fehler „timeout expired waiting for volumes to attach or mount for pod“ (Beim Anfügen oder Einbinden von Volumes für den Pod … ist eine Zeitüberschreitung aufgetreten) auftritt.|
|TSG057 – Fehler beim Starten des Controllerdiensts: System.TimeoutException| Verwenden Sie dieses Notebook, wenn Sie beim Starten des Controllerdiensts eine System.TimeoutException-Ausnahme auftritt.|
|TSG067: Die Einrichtung der Kube-Konfiguration konnte nicht abgeschlossen werden| Verwenden Sie dieses Notebook, wenn das Einrichten der Kube-Konfiguration fehlschlägt.|
|TSG074 – App-Deploys löschen| Verwenden Sie dieses Notebook, wenn beim Löschen von Apps in einem BDC-Cluster ein Problem auftritt.|
|TSG075: Der Fehler „FailedCreatePodSandBox“ ist aufgetreten, da „NetworkPlugin cni“ den Pod nicht einrichten konnte| Verwenden Sie dieses Notebook, wenn eine „FailedCreatePodSandBox“-Ausnahme auftritt, weil „NetworkPlugin cni“ den Pod nicht einrichten konnte.|
|TSG080 – Spark-Sitzungen mit azdata löschen| Verwenden Sie dieses Notebook, wenn beim Löschen von Spark-Sitzungen ein Problem auftritt.|
|TSG109 – Upgradetimeouts festlegen| Verwenden Sie dieses Notebook, wenn ein Problem mit einem BDC-Upgrade auftritt.|
|TSG110 – azdata gibt „ApiError“ zurück| Verwenden Sie dieses Notebook, wenn azdata „ApiError“ zurückgibt.|

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]?](big-data-cluster-overview.md).

