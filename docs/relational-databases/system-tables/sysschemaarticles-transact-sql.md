---
title: Sysschemaarticles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sysschemaarticles_TSQL
- sysschemaarticles
dev_langs:
- TSQL
helpviewer_keywords:
- sysschemaarticles system table
ms.assetid: 67a1c039-c283-4a9c-bacc-b9b3973590c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 37d064411927a112a50e9ff64a9e8a6dedefb3e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765408"
---
# <a name="sysschemaarticles-transact-sql"></a>sysschemaarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Protokolliert Artikel vom Typ schema only für Momentaufnahme- und Transaktionsveröffentlichungen. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Die Artikel-ID.|  
|**creation_script**|**nvarchar(255)**|Der Pfad und der Name eines Artikelschemaskripts, mit dem die Zieltabelle erstellt wird.|  
|**description**|**nvarchar(255)**|Der Beschreibungseintrag für den Artikel.|  
|**dest_object**|**sysname**|Der Name des Objekts in der Abonnementdatenbank, wenn der Artikel vom Typ schema only ist, wie z. B. eine gespeicherte Prozedur, eine Sicht oder eine UDF.|  
|**name**|**sysname**|Der Name des Artikels vom Typ schema only in einer Veröffentlichung.|  
|**Objekt-ID**|**int**|Der Objektbezeichner des Basisobjekts des Artikels. Dies kann der Objektbezeichner einer Prozedur, einer Sicht, einer indizierten Sicht oder einer UDF sein.|  
|**pubid**|**int**|Die ID für die Veröffentlichung.|  
|**pre_creation_cmd**|**tinyint**|Gibt die vom System durchzuführenden Schritte an, wenn es beim Anwenden der Momentaufnahme für diesen Artikel ein vorhandenes Objekt mit demselben Namen beim Abonnenten erkennt:<br /><br /> **0** = nothing.<br /><br /> **1** = Zieltabelle löschen.<br /><br /> **2** = entfernt die Zieltabelle.<br /><br /> **3** = schneidet die Zieltabelle.|  
|**status**|**int**|Das Bitmuster, das zum Anzeigen des Artikelstatus verwendet wird.|  
|**type**|**tinyint**|Der Wert, der den Typ des schema only-Artikels anzeigt:<br /><br /> **32** = gespeicherte Prozedur.<br /><br /> **64** = Sicht oder indizierte Sicht. <br /><br /> **96** = aggregate-Funktion.<br /><br /> **128** = Funktion.|  
|**schema_option**|**binary(8)**|Die Bitmaske der Option zur Schemagenerierung für den angegebenen Artikel. Sie gibt die automatische Erstellung der gespeicherten Prozedur in der Zieldatenbank für alle Anweisungen vom Typ CALL/MCALL/XCALL an. Hierbei kann es sich um das Ergebnis eines bitweisen logischen OR-Vorgangs von mindestens einem der folgenden Werte handeln:<br /><br /> **0 x 00** = deaktiviert Skripts durch den Momentaufnahme-Agent und verwendet *Creation_script*.<br /><br /> **0 x 01** = generiert die objekterstellung (CREATE TABLE, CREATE PROCEDURE usw.). Dies ist der Standardwert für alle Artikel mit gespeicherten Prozeduren.<br /><br /> **0 x 02** = generiert benutzerdefinierte gespeicherte Prozeduren für den Artikel aus, falls definiert.<br /><br /> **0 x 10** = generiert einen entsprechenden gruppierten Index.<br /><br /> **0 x 20** = konvertiert benutzerdefinierte Datentypen, um Datentypen in Basisdatentypen.<br /><br /> **0 x 40**= generiert entsprechende nicht gruppierte Indizes.<br /><br /> **0 x 80**= enthält die deklarierte referenziellen Integrität für die Primärschlüssel.<br /><br /> **0 x 73** = generiert die CREATE TABLE-Anweisung, erstellt gruppierte und nicht gruppierten Indizes, konvertiert benutzerdefinierte Datentypen in Basisdatentypen und generiert benutzerdefinierte gespeicherte Prozedurskripts, die auf dem Abonnenten angewendet werden. Dies ist der Standardwert für alle Artikel außer für Artikel mit gespeicherten Prozeduren.<br /><br /> **0 x 100**= repliziert Benutzertrigger für einen Tabellenartikel, falls definiert.<br /><br /> **0 x 200**= repliziert foreign Key-Einschränkungen. Wenn die referenzierte Tabelle, die nicht Teil einer Veröffentlichung ist, werden nicht alle foreign Key-Einschränkungen für eine veröffentlichte Tabelle repliziert.<br /><br /> **0 x 400**= repliziert Check-Einschränkungen.<br /><br /> **0 x 800**= repliziert Standardwerte.<br /><br /> **0 x 1000**= spaltensortierung repliziert.<br /><br /> **0 x 2000**= repliziert erweiterte Eigenschaften, die das Quellobjekt des veröffentlichten Artikels zugeordnet.<br /><br /> **0 x 4000**= repliziert eindeutige Schlüssel, wenn für einen Tabellenartikel definiert.<br /><br /> **0 x 8000**= repliziert den Primärschlüssel und eindeutige Schlüssel eines Tabellenartikels als Einschränkungen mithilfe von ALTER TABLE-Anweisungen.|  
|**dest_owner**|**sysname**|Der Besitzer der Tabelle in der Zieldatenbank|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
