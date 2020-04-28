---
title: Synchronisierungsmethode (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Synchronize method [ADO]
ms.assetid: 7af42866-7db2-4174-8251-388a2cf741f2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e280e5f8c9eda472c6448b199ffa94ac18c13751
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963265"
---
# <a name="synchronize-method-rds"></a>Synchronize-Methode (RDS)
Synchronisieren Sie das angegebene Recordset mit der Datenbank, die durch die Verbindungs Zeichenfolge für die Verwendung in ADO 2,5 und höher angegeben wird.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Synchronize(ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray, [lcid As Long], [pInformation)  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine Zeichenfolge, die zum Herstellen einer Verbindung mit dem OLE DB Anbieters verwendet wird, an den die Anforderung gesendet wird. Wenn ein Handler verwendet wird, kann der Handler die Verbindungs Zeichenfolge bearbeiten oder ersetzen.  
  
 *HandlerString*  
 Die Zeichenfolge identifiziert den Handler, der bei dieser Ausführung verwendet werden soll. Die Zeichenfolge enthält zwei Teile. Der erste Teil enthält den Namen (ProgID) des zu verwendenden Handlers. Der zweite Teil der Zeichenfolge enthält Argumente, die an den Handler übermittelt werden sollen. Wie die Argument Zeichenfolge interpretiert wird, ist handlerspezifisch. Die beiden Teile sind durch die erste Instanz eines Kommas in der Zeichenfolge getrennt (obwohl die Argument Zeichenfolge zusätzliche Kommas enthalten kann). Die Argumente sind optional.  
  
 *lSynchronizeOptions*  
 Eine Bitmaske der Synchronisierungs Optionen.  
  
 1 =*updatetransact* -Aktualisierungen der Datenbank werden in einer Transaktion umschließt. Die Transaktion wird abgebrochen, wenn ein Update fehlschlägt.  
  
 2 = Refresh*withupdate* bewirkt, dass Zeilen Status zurückgegeben werden, wenn weder Refresh-noch *Refresh* - *Konflikte* festgelegt sind.  
  
 4 =*Aktualisieren* das Recordset wird mit aktuellen Daten aus der Datenbank aktualisiert. Ausstehende Updates werden nicht an die Datenbank übermittelt. Wenn dieses Bit nicht festgelegt ist, wird das Recordset nicht aktualisiert, und alle ausstehenden Updates werden an die Datenbank übermittelt.  
  
 8 = Aktualisierungs*Konflikte* alle Zeilen mit ausstehenden Änderungen können nicht aktualisiert werden. Die Zeilen, die nicht aktualisiert werden konnten, werden mit den aktuellen Daten aus der Datenbank aktualisiert.  
  
 *ppRecordset*  
 Ein Zeiger auf das Recordset, das synchronisiert werden soll.  
  
 *pStatusArray*  
 Eine Variante, mit der ein sicheres Array von Zeilen Status für die von der Synchronisierung betroffenen Zeilen zurückgegeben wird. Nicht festgelegt, wenn keine der folgenden Synchronisierungs Optionen festgelegt ist: Refresh *withupdate, Update* *und* *Refresh* .  
  
 *lcid*  
 Die LCID, die verwendet wird, um Fehler zu erstellen, die in *pinformation*zurückgegeben werden.  
  
 *pInformation*  
 Ein Zeiger auf Informationen, die von **Execute**zurückgegeben werden. Wenn der Wert NULL ist, werden keine Fehlerinformationen zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der *handlerstring* -Parameter kann NULL sein. Was in diesem Fall geschieht, hängt von der Konfiguration des RDS-Servers ab. Die handlerzeichenfolge "msdfmap. Handler" gibt an, dass der von Microsoft bereitgestellte Handler ("msdfmap. dll") verwendet werden soll. Eine handlerzeichenfolge von "masdfmap. Handler, Sample. ini" gibt an, dass der msdfmap. dll-Handler verwendet werden sollte und dass das Argument "Sample. ini" an den Handler übermittelt werden soll. Msdfmap. dll interpretiert dann das Argument als Richtung, um die Verbindungs-und Abfrage Zeichenfolgen mit der Datei "Sample. ini" zu überprüfen.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


