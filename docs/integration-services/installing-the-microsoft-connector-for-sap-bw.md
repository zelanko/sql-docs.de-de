---
title: Installieren von Microsoft Connector für SAP BW | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 85ece835f73fa89f876b3bad9777e436cbffa8df
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58281284"
---
# <a name="installing-the-microsoft-connector-for-sap-bw"></a>Installieren von Microsoft Connector für SAP BW
  Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW für SQL Server 2016 ist eine Komponente des SQL Server 2016 Feature Pack. Zum Installieren des Connector für SAP BW und der zugehörigen Dokumentation laden Sie das Installationsprogramm von der [SQL Server 2016 Feature Pack-Webseite](https://go.microsoft.com/fwlink/?LinkId=746297)herunter, und führen Sie es aus.  

> [!IMPORTANT]
> Microsoft hat keine Einsicht in die Updatebereitstellung für die SAP BW-Connectors. Der Quellcode der SAP BW-Komponenten ist kein Eigentum von Microsoft, da diese von einem Drittanbieter entwickelt wurden. Aus diesem Grund kann Microsoft selbst keine Updates bereitstellen. Die neuesten SAP-Konnektivitätskomponenten können Sie bei Microsoft-ISV-Partnern wie [Theobald Software](https://theobald-software.com/en/xtract-is-productinfo.html) erwerben. Die ISV-Partner von Microsoft haben ihre SAP-Konnektivitätskomponenten für SSIS hinsichtlich einer Installation in Azure angepasst.

> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector für SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
> [!IMPORTANT]  
>  Das Extrahieren von Daten aus SAP NetWeaver BW erfordert zusätzliche SAP-Lizenzen. Stimmen Sie diese Anforderungen mit SAP ab.  
  
## <a name="required-sap-files"></a>Erforderliche SAP-Dateien  
 Wenn Sie [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW verwenden möchten, müssen Sie die SAP-Front-End-Software (SAP GUI) nicht auf dem lokalen Computer installieren.  
  
 Sie müssen jedoch die SAP .NET-Connector-Datei librfc32.dll im Ordner Windows in den Unterordner system kopieren. (In der Regel ist der Speicherort dieses Ordners **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Überlegungen für 64-Bit-Computer  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW bietet uneingeschränkte Unterstützung der 64-Bit-Version von [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. Auf einem 64-Bit-Computer gelten für [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW folgende zusätzliche Anforderungen:  
  
-   Wenn Sie Pakete im 64-Bit-Modus auf einem 64-Bit-Windows-Betriebssystem ausführen möchten, kopieren Sie die 64-Bit-Version der SAP GUI-Datei „librfc32.dll“ in den Unterordner **system32** des Windows-Ordners. (In der Regel ist der Speicherort dieser Datei **C:\Windows\system32**.)  
  
-   Wenn Sie Pakete im 32-Bit-Modus auf einem 64-Bit-Windows-Betriebssystem ausführen möchten, kopieren Sie die SAP GUI-Datei „librfc32.dll“ in den Unterordner **SysWow64** des Windows-Ordners. (In der Regel ist der Speicherort dieses Ordners **C:\Windows\SysWow64**.)  
  
  
