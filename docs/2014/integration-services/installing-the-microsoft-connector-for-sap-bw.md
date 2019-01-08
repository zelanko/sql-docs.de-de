---
title: Installieren von Microsoft Connector für 1.1 für SAP BW | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 80fef580e824fe3a668c5af990ef0955eebcad8d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52806482"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Installieren von Microsoft Connector 1.1 für SAP BW
  So installieren Sie die [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW und der zugehörigen Dokumentation laden, und führen Sie das Windows Installer-Paket aus der SQL Server Feature Pack-Webseite.  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
> [!IMPORTANT]  
>  Das Extrahieren von Daten aus SAP NetWeaver BW erfordert zusätzliche SAP-Lizenzen. Stimmen Sie diese Anforderungen mit SAP ab.  
  
## <a name="required-sap-files"></a>Erforderliche SAP-Dateien  
 Verwenden der [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 für SAP BW, Sie müssen nicht die SAP-Front-End-Software (SAP GUI) auf dem lokalen Computer zu installieren.  
  
 Sie müssen jedoch die SAP .NET-Connector-Datei librfc32.dll im Ordner Windows in den Unterordner system kopieren. (In der Regel ist der Speicherort dieses Ordners **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Überlegungen für 64-Bit-Computer  
 Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 für SAP BW unterstützt vollständig die 64-Bit-Version von [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. Auf einem 64-Bit-Computer die [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 für SAP BW hat die folgenden zusätzlichen Anforderungen:  
  
-   Wenn Sie Pakete im 64-Bit-Modus auf einem 64-Bit-Windows-Betriebssystem ausführen möchten, kopieren Sie die 64-Bit-Version der SAP GUI-Datei „librfc32.dll“ in den Unterordner **system32** des Windows-Ordners. (In der Regel ist der Speicherort dieser Datei **C:\Windows\system32**.)  
  
-   Wenn Sie Pakete im 32-Bit-Modus auf einem 64-Bit-Windows-Betriebssystem ausführen möchten, kopieren Sie die SAP GUI-Datei „librfc32.dll“ in den Unterordner **SysWow64** des Windows-Ordners. (In der Regel ist der Speicherort dieses Ordners **C:\Windows\SysWow64**.)  
  
  
