---
title: Herstellen einer Verbindung mit Datenquellen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: rothja
ms.author: jroth
ms.openlocfilehash: 1ef641bbfb94b8fde5f12af6cadd03f13fbfa91f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761166"
---
# <a name="connecting-to-data-sources"></a>Herstellen einer Verbindung mit Datenquellen
Ein ADO- **Verbindungs** Objekt stellt eine eindeutige Sitzung mit einer Datenquelle dar, einschließlich eines DBMS, eines Dateispeicher oder einer durch Trennzeichen getrennten Textdatei. Im Fall eines Client/Server-Datenbanksystems kann die ADO-Verbindung eine tatsächliche Netzwerkverbindung mit dem Server sein.  
  
 Das **Connection** -Objekt unterstützt verschiedene [Eigenschaften und Methoden](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) zum Angeben von Verbindungs Konfigurationen, öffnen und Schließen von Verbindungen, erstellen und Ausführen von Befehlen für die Datenquelle und Bereitstellen von Informationen zum Entwurf der zugrunde liegenden Datenquelle in Form von Schemarowsets usw. Abhängig von der vom Anbieter unterstützten Funktionalität sind einige Sammlungen, Methoden oder Eigenschaften eines **Verbindungs** Objekts möglicherweise nicht verfügbar.  
  
 Sie können eine Verbindung mit einer Datenquelle herstellen, indem Sie entweder ein **Verbindungs** Objekt oder ein **Recordset** -Objekt verwenden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verwenden eines Verbindungsobjekts](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [Verwenden eines Recordset-Objekts](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Erstellen einer Verbindungszeichenfolge](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Angeben von Verbindungseigenschaften](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Steuern von Transaktionen](../../../ado/guide/data/controlling-transactions-ado.md)
