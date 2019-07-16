---
title: Zertifikatbereitstellung - Analytics Platform System | Microsoft-Dokumentation
description: Zertifikatbereitstellung in Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0da49afe13ab0f8cc92e8dd58e78f40564ff53c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960221"
---
# <a name="certificate-provisioning-in-analytics-platform-system"></a>Zertifikatbereitstellung in Analytics Platform System
Die **PDW-Zertifikatbereitstellung** auf der Seite das Analytics Platform System**Configuration Manager** importiert oder das Zertifikat ein, die PDW entfernt. 

Verwenden, ein Zertifikat zum Verschlüsseln von Verbindungen kann Unterstützung der sicheren Kommunikation mit dem Steuerungsknoten über SQL Server-Clients, Tools, mit denen die SQL Server-PDW-Treiber, die [Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md), und lädt Sie Integration Services. 
  
## <a name="prerequisites"></a>Vorraussetzungen  
Führen Sie bevor Sie das Zertifikat installiert wird folgende Schritte aus:  
  
1.  Ein gesichertes Zertifikat zu erhalten. Wenn Sie weitere Informationen zum Abrufen eines sicheren Zertifikats benötigen, wenden Sie sich an Microsoft Support.  
  
2.  Speichern Sie das Zertifikat mit dem Steuerungsknoten in eine kennwortgeschützte PFX-Datei.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>Aus Sicherheitsgründen erhalten Sie ein vertrauenswürdiges Zertifikat  
SQL Server PDW unterstützt die Verwendung eines Zertifikats zur Verschlüsselung von Verbindungen mit dem Steuerungsknoten; Verbindungen, einschließlich der **Verwaltungskonsole**.  
  
In der Standardeinstellung die **Verwaltungskonsole** enthält ein selbst signiertes Zertifikat, das Datenschutz, aber keine Serverauthentifizierung bereitstellt. Diese lassen Kommunikation anfällig für Man-in-the-Middle-Angriffe. Internet Explorer gibt den Fehler zurück, wenn ein Benutzer auf die Verwaltungskonsole verbunden ist mit dem selbstsignierten Zertifikat: "Es ist ein Problem mit dem Sicherheitszertifikat der Website".  
  
Auch wenn die Verbindung über das selbstsignierte Zertifikat gesendeten Daten zwischen dem Client und Server verschlüsselt, ist die Verbindung immer noch durch Angreifer gefährdet.  
  
> [!WARNING]  
> Appliance-Administratoren sollten sofort ein Zertifikat zu erhalten, ist mit einer vertrauenswürdigen Zertifizierungsstelle, die von Clients, um eine sichere Verbindung hergestellt, und entfernen den Fehler, den Internet Explorer meldet erkannt, verkettet.  
  
Zertifizierungspfad muss den vollständig qualifizierten Domänennamen, der mit dem Steuerungsknoten IP-Adresse des Clusters (empfohlen) zugeordnet ist oder der Name, der in ihren Browser Adresse Balken den Zugriff auf die Benutzer eingeben enthalten die **Verwaltungskonsole**.  
  
Verwenden Sie das Analytics Platform System**Configuration Manager** hinzufügen oder entfernen das vertrauenswürdige Zertifikat. Direkt mithilfe des Konfigurationstools für Microsoft Windows HTTP-Dienste-Zertifikat (**winHttpCertCfg.exe**) zum Verwalten des Zertifikats werden nicht unterstützt.  
  
## <a name="import-or-remove-the-certificate"></a>Importieren Sie oder entfernen Sie das Zertifikat  
Die folgenden Anweisungen zeigen, wie zum Importieren oder entfernen Sie das Zertifikat für die Appliance.  
  
### <a name="to-import-the-certificate"></a>Zum Importieren des Zertifikats  
  
1.  Starten Sie den **Konfigurations-Manager**.  
Weitere Informationen finden Sie unter [Starten des Konfigurations-Managers &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  

2.  Im linken Bereich die **Configuration Manager**, erweitern Sie **Parallel Data Warehouse-Topologie**, und klicken Sie dann auf **Zertifikate**.  
  
3.  Wählen Sie **Importieren eines Zertifikats, und konfigurieren Sie die Appliance für dessen Verwendung**, und klicken Sie dann auf **Durchsuchen** , navigieren Sie zu, und wählen Sie die Zertifikatdatei.  
  
4.  Geben Sie das Kennwort für das Zertifikat in der **Kennwort** Feld.  
  
5.  Klicken Sie auf **übernehmen** zum Konfigurieren des verwaltungszertifikats für die Appliance.  
  
SQL Server PDW aktuellen Verbindung nicht anhand des importierten Zertifikats verschlüsselt, aber das Zertifikat für neue Verbindungen verwenden soll.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>So entfernen Sie die zuvor importierte Zertifikat  
  
1.  Starten Sie den **Konfigurations-Manager**. 

<!-- MISSING LINKS
For more information, see [Launch the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager-analytics-platform-system.md).  
-->
  
2.  Im linken Bereich die **Configuration Manager**, erweitern Sie **Parallel Data Warehouse-Topologie**, und klicken Sie dann auf **Zertifikate**.  
  
3.  Wählen Sie **entfernen Sie alle Zertifikate in der Appliance bereitgestellt**.  
  
4.  Klicken Sie auf **übernehmen** So entfernen Sie das zuvor importierte Zertifikat aus der Appliance.  
  
SQL Server PDW zum Verschlüsseln von aktuellen Verbindungen weiterhin, aber es wird nicht für neue Verbindungen verwenden Sie das Zertifikat entfernte.  
  
![DWConfig-Anwendung-PDW-Zertifikat](media/dwconfig-appl-pdw-cert.png "DWConfig Appliance PDW-Zertifikat")  
  
## <a name="see-also"></a>Siehe auch  
[Starten Sie den Konfigurations-Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
