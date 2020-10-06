---
description: Konfigurieren von virtuellen Servern unter IIS
title: Konfigurieren virtueller Server auf IIS | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: rothja
ms.author: jroth
ms.openlocfilehash: b8e1899e6393f1dc7ae4d9b2080d349bbedf1d41
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724791"
---
# <a name="configuring-virtual-servers-on-iis"></a>Konfigurieren von virtuellen Servern unter IIS
Wenn Sie virtuelle Server in Internetinformationsdienste 4,0 erstellen, sind die folgenden beiden zusätzlichen Schritte erforderlich, um den virtuellen Server für die Zusammenarbeit mit RDS zu konfigurieren:  
  
1.  Wenn Sie den Server einrichten, aktivieren Sie "Execute Execute Access".  
  
2.  Verschieben Sie msadcs.dll zu *vroot*\MSADC, wobei *vroot das Basis* Verzeichnis des virtuellen Servers ist.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](./rds-fundamentals.md)