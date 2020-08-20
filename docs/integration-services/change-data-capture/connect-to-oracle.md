---
description: Herstellen einer Verbindung mit Oracle
title: Herstellen einer Verbindung mit Oracle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c628f77c74c16bd196a496e7cacf27a0f2904e12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88496261"
---
# <a name="connect-to-oracle"></a>Herstellen einer Verbindung mit Oracle

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Wenn Sie die in der CDC-Instanz verwendeten Tabellen zum ersten Mal hinzufügen oder bearbeiten, werden Sie möglicherweise aufgefordert, eine Verbindung mit der Oracle-Datenbank herzustellen. Geben Sie die Anmeldeinformationen eines Oracle-Benutzers ein, der auf das Schema der aufzuzeichnenden Tabellen zugreifen kann. Geben Sie in diesem Dialogfeld Folgendes ein:  
  
 **Authentifizierung**  
  
 Wählen Sie eines der folgenden Szenarien aus:  
  
-   **Windows-Authentifizierung**: Wählen Sie diese Option, um die aktuellen Anmeldeinformationen für die Windows-Domäne zu verwenden. Sie können diese Option nur verwenden, wenn die Oracle-Datenbank für die Nutzung der Windows-Authentifizierung konfiguriert ist.  
  
-   **Oracle Authentication**: Wenn Sie diese Option aktivieren, müssen Sie **Benutzername** und **Kennwort** für den Benutzer der Oracle-Datenbank eingeben, mit der Sie eine Verbindung herstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Tabellen zu einer CDC-Instanz](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  
