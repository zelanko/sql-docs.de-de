---
title: Zertifikatverwaltung (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/16/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 88e35bc2589f30a0fa3d6b707d66aa25325dc89e
ms.sourcegitcommit: b51edbe07a0a2fdb5f74b5874771042400baf919
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55088990"
---
# <a name="certificate-management-sql-server-configuration-manager"></a>Zertifikatverwaltung (SQL Server-Konfigurations-Manager)

In diesem Thema erfahren Sie, wie Zertifikate in Ihrer Topologie der SQL Server-Always On-Failovercluster bzw. -Verfügbarkeitsgruppen bereitgestellt und verwaltet werden.

SSL/TLS-Zertifikate werden oft dazu verwendet, den Zugriff auf SQL Server zu sichern. Bei früheren Versionen von SQL Server war es für Organisationen mit großen SQL Server-Umgebungen viel Aufwand, ihre Infrastruktur der SQL Server-Zertifikate zu pflegen. Hierzu wurden häufig Skripts entwickelt und manuelle Befehle ausgeführt. Ab SQL Server 2019 ist die Zertifikatverwaltung im SQL Server-Konfigurations-Manager integriert, was allgemeine Aufgaben wie die Folgenden vereinfacht: 

* Anzeigen und Überprüfen der auf einer SQL Server-Instanz installierten Zertifikate 
* Identifizieren der bald ablaufenden Zertifikate 
* Bereitstellen von Zertifikaten für Computer von Verfügbarkeitsgruppen auf dem Knoten mit dem primären Replikat 
* Bereitstellen von Zertifikaten für Computer einer Failoverclusterinstanz auf dem aktiven Knoten

> [!NOTE]
> Sie können die Zertifikatverwaltung im SQL Server-Konfigurations-Manager mit früheren Versionen von SQL Server verwenden, beginnend mit SQL Server 2008.

##  <a name="provision-single-server-cert"></a>So installieren Sie ein Zertifikat für eine einzelne SQL Server-Instanz  
  
1. Erweitern Sie im SQL Server-Konfigurations-Manager im Konsolenbereich den Knoten **SQL Server-Netzwerkkonfiguration**.  
  
2. Klicken Sie mit der rechten Maustaste auf **Protokolle für** *&lt;Instanzname&gt;* und dann auf **Eigenschaften**.  
  
3. Wählen Sie die Registerkarte **Zertifikat** und anschließend **Importieren** aus.  
  
4. Klicken Sie auf **Durchsuchen** und dann auf die Zertifikatsdatei.  
  
5. Klicken Sie auf **Weiter**, um das Zertifikat zu überprüfen. Wenn keine Fehler vorliegen, klicken Sie auf **Weiter**, um das Zertifikat in die lokale Instanz zu importieren.  
  
 
##  <a name="provision-failover-cluster-cert"></a>So installieren Sie ein Zertifikat in einer Failoverclusterkonfiguration  
  
1. Erweitern Sie im SQL Server-Konfigurations-Manager im Konsolenbereich den Knoten **SQL Server-Netzwerkkonfiguration**.
  
2. Klicken Sie mit der rechten Maustaste auf **Protokolle für** *&lt;Instanzname&gt;* und dann auf **Eigenschaften**. 

3. Wählen Sie die Registerkarte **Zertifikat** und anschließend **Importieren** aus.

4. Wählen Sie den Zertifikattyp aus, und geben Sie an, ob dieser nur für den aktuellen Knoten oder für jeden einzelnen Clusterknoten importiert werden soll.

5. Zur Installation für einen einzelnen Knoten klicken Sie auf **Durchsuchen** und anschließend auf die Zertifikatdatei. Fahren Sie dann mit Schritt 8 fort.

6. Klicken Sie zur Installation eines Zertifikats für jeden Knoten auf **Weiter**, um die Knoten möglicher Besitzer aufzulisten. Mögliche Besitzer für die aktuelle SQL Server-FCI-Instanz sind vorab ausgewählt.

7. Klicken Sie auf **Weiter**, um das zu importierende Zertifikat auswählen.

8. Geben Sie bei Aufforderung das Kennwort ein. Achten Sie nach der Überprüfung auf mögliche Warn- oder Fehlermeldungen.

9. Klicken Sie auf **Weiter**, um die ausgewählten Zertifikate zu importieren.

> [!NOTE]
> Führen Sie diese Schritte im aktiven Knoten der SQL Server-Failoverclusterinstanz aus. Benutzer müssen über Administratorberechtigungen auf allen Clusterknoten verfügen.

##  <a name="provision-availability-group-cert"></a>So installieren Sie ein Zertifikat in einer Verfügbarkeitsgruppenkonfiguration  
  
1. Erweitern Sie im SQL Server-Konfigurations-Manager im Konsolenbereich den Knoten **SQL Server-Netzwerkkonfiguration**.
  
2. Klicken Sie mit der rechten Maustaste auf **Protokolle für** *&lt;Instanzname&gt;* und dann auf **Eigenschaften**.  
  
3. Wählen Sie die Registerkarte **Zertifikat** und anschließend **Importieren** aus.  
  
4. Klicken Sie auf den Zertifikattyp und anschließend auf **Weiter**, um aus der Liste der bekannten Verfügbarkeitsgruppen auszuwählen.  

5. Klicken Sie auf **Weiter**, um Zertifikate für einen bestimmten Replikatknoten auszuwählen. Zertifikate müssen einen Dateinamen aufweisen, der den NetBIOS-Namen der Knoten entspricht.

6. Klicken Sie auf **Weiter**, um das Zertifikat für jeden Knoten zu importieren.


> [!NOTE]
> Führen Sie diese Schritte im Knoten mit dem primären Replikat der Verfügbarkeitsgruppe aus. Benutzer müssen über Administratorberechtigungen auf allen Clusterknoten verfügen.

