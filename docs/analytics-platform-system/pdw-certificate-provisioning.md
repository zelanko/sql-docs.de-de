---
title: PDW-Zertifikatbereitstellung
description: Die Seite PDW-Zertifikat Bereitstellung des Analytics Platform System Configuration Manager importiert oder entfernt das von der PDW-Region verwendete Zertifikat.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 676335fb8ee4aac5906c61084c28cd94cf8ea815
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400894"
---
# <a name="pdw-certificate-provisioning---analytics-platform-system"></a>PDW-Zertifikat Bereitstellung: Analytics Platform System
Die Seite **PDW-Zertifikat Bereitstellung** des Analytics Platform System **Configuration Manager** importiert oder entfernt das von der PDW-Region verwendete Zertifikat. Mithilfe von kann ein Zertifikat zum Verschlüsseln von Verbindungen die Kommunikation mit dem Steuerungs Knoten über SQL Server Clients, Tools, die die SQL Server PDW-Treiber, die- [Verwaltungskonsole](monitor-the-appliance-by-using-the-admin-console.md)und die Integration Services lädt, sichern.  
  
## <a name="prerequisites"></a>Voraussetzungen  
Vor der Installation des Zertifikats führen Sie die folgenden Schritte aus:  
  
1.  Abrufen eines sicheren Zertifikats Wenn Sie weitere Informationen dazu benötigen, wie Sie ein sicheres Zertifikat erhalten, wenden Sie sich an Microsoft-Support.  
  
2.  Speichern Sie das Zertifikat auf dem Steuerungs Knoten in einer Kenn Wort geschützten PFX-Datei.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>Aus Sicherheitsgründen sollten Sie ein vertrauenswürdiges Zertifikat abrufen.  
SQL Server PDW unterstützt die Verwendung eines Zertifikats zum Verschlüsseln von Verbindungen mit dem Steuer Knoten. einschließen von Verbindungen mit der **Verwaltungskonsole**.  
  
Standardmäßig enthält die- **Verwaltungskonsole** ein selbst signiertes Zertifikat, das Datenschutz, aber keine Server Authentifizierung bereitstellt. Dies kann die Kommunikation für einen man-in-the-Middle-Angriff anfällig machen. Wenn ein Benutzer mithilfe des selbst signierten Zertifikats eine Verbindung mit der Verwaltungskonsole herstellt, gibt Internet Explorer den folgenden Fehler zurück: "Es liegt ein Problem mit dem Sicherheitszertifikat dieser Website vor".  
  
Obwohl bei der Verbindung über das selbst signierte Zertifikat in-Flight-Daten zwischen dem Client und dem Server verschlüsselt werden, ist die Verbindung von Angreifern immer noch gefährdet.  
  
> [!WARNING]  
> Geräte Administratoren sollten sofort ein Zertifikat abrufen, das mit einer vertrauenswürdigen Zertifizierungsstelle verkettet ist, die von Clients erkannt wird, um eine sichere Verbindung herzustellen und den Fehler zu entfernen, den Internet Explorer meldet.  
  
Der Zertifizierungspfad muss den voll qualifizierten Domänen Namen enthalten, der der IP-Adresse des Kontroll Knoten Clusters (empfohlen) zugeordnet ist, oder den Namen, den die Benutzer in die Adressleiste Ihres Browsers eingeben, um auf die **Verwaltungskonsole**zuzugreifen.  
  
Verwenden Sie das**Configuration Manager** Analytics Platform System, um das vertrauenswürdige Zertifikat hinzuzufügen oder zu entfernen. Die direkte Verwendung des Microsoft Windows HTTP Services Certificate Configuration Tool (**Winhttpcertcfg. exe**) zum Verwalten des Zertifikats wird nicht unterstützt.  
  
## <a name="import-or-remove-the-certificate"></a>Importieren oder Entfernen des Zertifikats  
Die folgenden Anweisungen zeigen, wie das Gerätezertifikat importiert oder entfernt wird.

> [!WARNING]
> Zum Erneuern eines abgelaufenen Zertifikats müssen Sie das vorhandene Zertifikat entfernen, bevor Sie das neue Zertifikat importieren.
  
### <a name="to-import-the-certificate"></a>So importieren Sie das Zertifikat  
  
1.  Starten Sie die **Configuration Manager**. Weitere Informationen finden Sie unter [Start the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Erweitern Sie im linken Bereich des **Configuration Manager**die Option **parallele Data Warehouse Topologie**, und klicken Sie dann auf **Zertifikate**.  
  
3.  Wählen Sie Zertifikat importieren aus, und **Konfigurieren Sie die Appliance für deren Verwendung**, und klicken Sie dann auf **Durchsuchen** , um die Zertifikat Datei zu suchen und auszuwählen.  
  
4.  Geben Sie im Feld **Kennwort** das Kennwort für das Zertifikat ein.  
  
5.  Klicken **Sie auf über** nehmen, um das Zertifikat für das Gerät zu konfigurieren.  
  
SQL Server PDW verschlüsselt die aktuelle Verbindung nicht mithilfe des importierten Zertifikats, sondern verwendet das Zertifikat für neue Verbindungen.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>So entfernen Sie das zuvor importierte Zertifikat  
  
1.  Starten Sie die **Configuration Manager**. Weitere Informationen finden Sie unter [Start the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Erweitern Sie im linken Bereich des **Configuration Manager**die Option **parallele Data Warehouse Topologie**, und klicken Sie dann auf **Zertifikate**.  
  
3.  Wählen Sie **alle in der Appliance bereitgestellten Zertifikate entfernen aus**.  
  
4.  Klicken **Sie auf über** nehmen, um das zuvor importierte Zertifikat aus dem Gerät zu entfernen.  
  
Die aktuellen Verbindungen werden von SQL Server PDW weiterhin verschlüsselt, aber das entfernte Zertifikat wird für neue Verbindungen nicht verwendet.  
  
![DWConfig-Anwendung, PDW-Zertifikat](./media/pdw-certificate-provisioning/SQL_Server_PDW_DWConfig_ApplPDWCert.png "SQL_Server_PDW_DWConfig_ApplPDWCert")  
  
## <a name="see-also"></a>Weitere Informationen  
[Starten Sie die Configuration Manager &#40;Analytics-Platt Form System&#41;](launch-the-configuration-manager.md)  
<!-- MISSING LINKS [HDInsight Certificate Provisioning &#40;Analytics Platform System&#41;](hdinsight-certificate-provisioning.md)  -->  
  
