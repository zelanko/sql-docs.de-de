---
description: Flush-Methode (ADO)
title: Flush-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
author: rothja
ms.author: jroth
ms.openlocfilehash: a76817a6219a506ef1158e94b7ffbf2fae6f629f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88972981"
---
# <a name="flush-method-ado"></a>Flush-Methode (ADO)
Erzwingt den Inhalt des verbleibenden [Streams](./stream-object-ado.md) im ADO-Puffer für das zugrunde liegende Objekt, dem der **Stream** zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode kann verwendet werden, um den Inhalt des Streampuffers an das zugrunde liegende Objekt zu senden, z. b. den Knoten oder die Datei, der durch die URL dargestellt wird, die die Quelle des Daten **Strom** Objekts ist. Diese Methode sollte aufgerufen werden, wenn Sie sicherstellen möchten, dass alle Änderungen, die an den Inhalten eines **Streams** vorgenommen wurden, geschrieben wurden. Allerdings ist es in der Regel nicht **erforderlich, eine Leerung aufzurufen**, da ADO den Puffer fortlaufend im Hintergrund leert. Änderungen am Inhalt eines **Streams** werden automatisch vorgenommen, nicht zwischengespeichert **, bis der** Lösch Modus aufgerufen wird.  
  
 Durch das Schließen eines **Streams** mit der [Close](./close-method-ado.md) -Methode wird der Inhalt eines **Streams** automatisch geleert. das Löschen **muss unmittelbar vor** dem **Schließen**nicht explizit aufgerufen werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)