---
title: Installieren von Microsoft Connector für 1,1 SAP BW | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0e43a45f9b21e631638dec43a8a126b4f007429d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62767752"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Installieren von Microsoft Connector 1.1 für SAP BW
  Um den [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1,1 für SAP BW und seine Dokumentation zu installieren, laden Sie das Windows Installer-Paket von der SQL Server Feature Pack-Webseite herunter, und führen Sie es aus.  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
> [!IMPORTANT]  
>  Das Extrahieren von Daten aus SAP NetWeaver BW erfordert zusätzliche SAP-Lizenzen. Stimmen Sie diese Anforderungen mit SAP ab.  
  
## <a name="required-sap-files"></a>Erforderliche SAP-Dateien  
 Wenn Sie den [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1,1 für SAP BW verwenden möchten, müssen Sie die SAP-Front-End-Software (SAP GUI) nicht auf dem lokalen Computer installieren.  
  
 Sie müssen jedoch die SAP .NET-Connector-Datei librfc32.dll im Ordner Windows in den Unterordner system kopieren. (In der Regel ist der Speicherort dieses Ordners **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Überlegungen für 64-Bit-Computer  
 Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1,1 für SAP BW unterstützt die 64-Bit-Version [!INCLUDE[msCoName](../includes/msconame-md.md)] von Windows vollständig. Auf einem 64-Bit-Computer weist [!INCLUDE[msCoName](../includes/msconame-md.md)] der Connector 1,1 für SAP BW die folgenden zusätzlichen Anforderungen auf:  
  
-   Wenn Sie Pakete im 64-Bit-Modus auf einem 64-Bit-Windows-Betriebssystem ausführen möchten, kopieren Sie die 64-Bit-Version der SAP GUI-Datei „librfc32.dll“ in den Unterordner **system32** des Windows-Ordners. (In der Regel ist der Speicherort dieser Datei **C:\Windows\system32**.)  
  
-   Wenn Sie Pakete im 32-Bit-Modus auf einem 64-Bit-Windows-Betriebssystem ausführen möchten, kopieren Sie die SAP GUI-Datei „librfc32.dll“ in den Unterordner **SysWow64** des Windows-Ordners. (In der Regel ist der Speicherort dieses Ordners **C:\Windows\SysWow64**.)  
  
  
