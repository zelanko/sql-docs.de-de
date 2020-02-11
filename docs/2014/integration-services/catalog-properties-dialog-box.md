---
title: Katalog Eigenschaften (Dialog Feld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.iscatalogprop.general.f1
- sql12.ssis.ssms.iscreatecatalog.f1
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8d3492cce19906322ef9b420718aae0ae9e0e62d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66061113"
---
# <a name="catalog-properties-dialog-box"></a>Katalogeigenschaften (Dialogfeld)
  Verwenden Sie das Dialogfeld Katalogeigenschaften, um den SSISDB-Katalog zu konfigurieren. Katalog Eigenschaften definieren, wie sensible Daten verschlüsselt werden, wie Vorgänge und projektversionsversionsdaten aufbewahrt werden und wann ein Timeout bei Überprüfungs Vorgängen auftritt. Der ssisdb-Katalog ist ein zentraler Speicher-und Verwaltungs [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Punkt für Projekte, Pakete, Parameter und Umgebungen.  
  
 Sie können Katalogeigenschaften auch in der catalog.catalog_property-Sicht anzeigen und die Eigenschaften mit der gespeicherten catalog.configure_catalog-Prozedur festlegen. Weitere Informationen finden Sie unter [catalog.catalog_properties &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) und [catalog.configure_catalog &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 Weitere Informationen zum Erstellen eines SSISDB-Katalogs finden Sie unter [Erstellen des SSIS-Katalogs](catalog/ssis-catalog.md).  
  
 **Was möchten Sie tun?**  
  
-   [Dialog Feld "Katalog Eigenschaften" öffnen](#open_dialog)  
  
-   [Konfigurieren der Optionen](#options)  
  
##  <a name="open_dialog"></a>Dialog Feld "Katalog Eigenschaften" öffnen  
  
1.  Öffnen Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Stellen Sie eine Verbindung mit einer Microsoft SQL Server-Datenbank-Engine her.  
  
3.  Erweitern Sie im Objekt-Explorer den Knoten **Integration Services** , klicken Sie mit der rechten Maustaste auf den Knoten **SSISDB**, und klicken Sie anschließend auf **Eigenschaften**.  
  
##  <a name="options"></a> Konfigurieren der Optionen  
  
### <a name="options"></a>Tastatur  
 In der folgenden Tabelle werden spezifische Eigenschaften in dem Dialogfeld und die entsprechenden Eigenschaften in der catalog.catalog_property-Sicht beschrieben.  
  
|Eigenschaftsname (Dialogfeld Katalogeigenschaften)|Eigenschaftsname (catalog.catalog_property-Sicht)|BESCHREIBUNG|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|Name des Verschlüsselungsalgorithmus|ENCRYPTION_CLEANUP_ENABLED|Gibt den Verschlüsselungstyp an, der zur Verschlüsselung der sensiblen Parameterwerte im Katalog verwendet wird. Folgende Werte sind möglich:<br /><br /> **DES**<br /><br /> **TRIPLE_DES**<br /><br /> **TRIPLE_DES_3KEY**<br /><br /> **DESPX**<br /><br /> **AES_128**<br /><br /> **AES_192**<br /><br /> **AES_256** (Standard)|  
|Überprüfungstimeout (Sekunden)|VALIDATION_TIMEOUT|Geben Sie die maximale Ausführungsdauer in Sekunden ab, bevor eine Projektüberprüfung oder Paketüberprüfung beendet wird. Der Standardwert beträgt 300 Sekunden.<br /><br /> Die Validierung ist ein asynchroner Vorgang. Je größer das Projekt oder das Paket ist, desto länger dauert die Validierung.<br /><br /> Informationen zum Überprüfen von Projekten und Paketen finden Sie unter [Integration Services Data Types in Expressions](expressions/integration-services-data-types-in-expressions.md).|  
|Protokolle regelmäßig bereinigen|OPERATION_CLEANUP_ENABLED|Legen Sie die Eigenschaft auf "True" fest, um anzugeben, dass der SQL Server-Agentauftrag, die Vorgangsbereinigung, ausgeführt wird. Legen Sie die Eigenschaft andernfalls auf "False" fest.|  
|Beibehaltungsdauer (Tage)|RETENTION_WINDOW|Geben Sie das maximale Alter von zulässigen Vorgangsdaten (in Tagen) an. Daten, die älter als die angegebene Anzahl von Tagen sind, werden vom SQL-Agentauftrag, durch die Vorgangsbereinigung, entfernt.|  
|Maximale Anzahl der Versionen pro Projekt|MAX_PROJECT_VERSIONS|Geben Sie an, wie viele Versionen eines Projekts im Katalog gespeichert werden. Wenn die maximale Anzahl überschritten wird, werden frühere Versionen von Projekten bei der Bereinigung von Projektversionen entfernt.|  
  
  
