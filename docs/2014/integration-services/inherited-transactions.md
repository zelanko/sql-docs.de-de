---
title: Vererbte Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], inherited
- child packages
- inherited transactions [Integration Services]
ms.assetid: 90db5564-d41e-4cfe-8c9e-4e68d41eff1c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d8e22375e660e6bcd55c8075edaaba067160279d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66058055"
---
# <a name="inherited-transactions"></a>Vererbte Transaktionen
  Ein Paket kann mithilfe des Tasks "Paket ausführen" ein anderes Paket ausführen. Das untergeordnete Paket, d. h. das von dem Task Paket ausführen ausgeführte Paket, kann seine eigene Pakettransaktion erstellen oder aber die Pakettransaktion des übergeordneten Pakets erben.  
  
 Ein untergeordnetes Paket erbt die übergeordnete Pakettransaktion, wenn die beiden folgenden Bedingungen erfüllt sind:  
  
-   Das Paket wird durch einen Task Paket ausführen aufgerufen.  
  
-   Der Task Paket ausführen, der das Paket aufgerufen hat, nimmt ebenfalls an der übergeordneten Pakettransaktion teil.  
  
 Container und Tasks des untergeordneten Pakets können nicht an der übergeordneten Pakettransaktion teilnehmen, es sei denn, das untergeordnete Paket nimmt selbst an der Transaktion teil.  
  
## <a name="illustration-of-package-transactions"></a>Abbildung von Pakettransaktionen  
 Im folgenden Diagramm sind drei Pakete zu sehen, die Transaktionen verwenden. Jedes Paket enthält zahlreiche Tasks. Um das Verhalten der Transaktionen zu verdeutlichen, werden nur die Tasks Paket ausführen gezeigt. Das Paket A führt die Pakete B und C aus. Das Paket B wiederum führt die Pakete D und E aus, und das Paket C führt das Paket F aus.  
  
 Die Pakete und Tasks besitzen die folgenden Transaktionsattribute:  
  
-   **TransactionOption** ist für die Pakete A und C auf **Required** festgelegt.  
  
-   **TransactionOption** ist für die Pakete B und D sowie für die Tasks Paket ausführen B, Paket ausführen D und Paket ausführen F auf **Supported** festgelegt.  
  
-   **TransactionOption** ist für das Paket E sowie für die Tasks Paket ausführen C und Paket ausführen E auf **NotSupported** festgelegt.  
  
 ![Fluss von geerbten Transaktionen](media/mw-dts-executepack.gif "Flow of inherited transactions")  
  
 Nur die Pakete B, D und F können Transaktionen von ihren übergeordneten Paketen erben.  
  
 Die Pakete B und D erben die Transaktion, die von Paket A gestartet wurde.  
  
 Das Paket F erbt die Transaktion, die von Paket C gestartet wurde.  
  
 Die Pakete A und C steuern ihre eigenen Transaktionen.  
  
 Das Paket E verwendet keine Transaktionen.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Konfigurieren eines Pakets für die Verwendung von Transaktionen](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
