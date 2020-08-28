---
description: Herstellen einer Verbindung mit Datenquellen
title: Herstellen einer Verbindung mit Datenquellen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: rothja
ms.author: jroth
ms.openlocfilehash: 988eef3a3eb706480e50f0feb6d2fe363b4faabd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991521"
---
# <a name="connecting-to-data-sources"></a>Herstellen einer Verbindung mit Datenquellen
Ein ADO- **Verbindungs** Objekt stellt eine eindeutige Sitzung mit einer Datenquelle dar, einschließlich eines DBMS, eines Dateispeicher oder einer durch Trennzeichen getrennten Textdatei. Im Fall eines Client/Server-Datenbanksystems kann die ADO-Verbindung eine tatsächliche Netzwerkverbindung mit dem Server sein.  
  
 Das **Connection** -Objekt unterstützt verschiedene [Eigenschaften und Methoden](../../reference/ado-api/connection-object-properties-methods-and-events.md) zum Angeben von Verbindungs Konfigurationen, öffnen und Schließen von Verbindungen, erstellen und Ausführen von Befehlen für die Datenquelle und Bereitstellen von Informationen zum Entwurf der zugrunde liegenden Datenquelle in Form von Schemarowsets usw. Abhängig von der vom Anbieter unterstützten Funktionalität sind einige Sammlungen, Methoden oder Eigenschaften eines **Verbindungs** Objekts möglicherweise nicht verfügbar.  
  
 Sie können eine Verbindung mit einer Datenquelle herstellen, indem Sie entweder ein **Verbindungs** Objekt oder ein **Recordset** -Objekt verwenden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verwenden eines Connection-Objekts](./using-a-connection-object.md)  
  
-   [Verwenden eines Recordset-Objekts](./using-a-recordset-object.md)  
  
-   [Erstellen einer Verbindungszeichenfolge](./creating-a-connection-string.md)  
  
-   [Angeben von Verbindungseigenschaften](./specifying-connection-properties.md)  
  
-   [Steuern von Transaktionen](./controlling-transactions-ado.md)