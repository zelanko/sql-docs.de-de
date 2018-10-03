---
title: Sysmergeschemaarticles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sysmergeschemaarticles_TSQL
- sysmergeschemaarticles
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergeschemaarticles system table
ms.assetid: b5085979-2f76-48e1-bf3b-765a84003dd9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 397608f755e302c1500cb2b94f18f3e8cbc98ffe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721548"
---
# <a name="sysmergeschemaarticles-transact-sql"></a>sysmergeschemaarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Verfolgt Artikel vom Typ schema only für die Mergereplikation nach. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des Artikels vom Typ schema only in der Mergeveröffentlichung.|  
|**type**|**tinyint**|Zeigt den Typ des Artikels vom Typ schema only an, der einen der folgenden Werte annehmen kann:<br /><br /> **0 x 20** = gespeicherte Prozedur Schema only-Artikel.<br /><br /> **0 x 40** = View Schema only-Artikel oder Artikel mit indizierter Sicht Schema only.|  
|**Objekt-ID**|**int**|Der Objektbezeichner des Basisobjekts des Artikels. Kann der Objektbezeichner einer Prozedur, einer Sicht, einer indizierten Sicht oder einer benutzerdefinierten Funktion sein.|  
|**artid**|**uniqueidentifier**|Die Artikel-ID.|  
|**description**|**nvarchar(255)**|Die Beschreibung des Artikels.|  
|**pre_creation_command**|**tinyint**|Standardaktion, die ausgeführt wird, wenn der Artikel in der Abonnementdatenbank erstellt wird:<br /><br /> **0 =** keine - Wenn die Tabelle bereits auf dem Abonnenten vorhanden ist keine Aktion ausgeführt.<br /><br /> **1** = Drop - Tabelle gelöscht, bevor Sie neu zu erstellen.<br /><br /> **2** = löschen: ein Löschvorgang wird basierend auf der WHERE-Klausel im Teilmengenfilter ausgegeben.<br /><br /> **3** = Abschneiden-identisch mit **2**, jedoch werden Seiten statt Zeilen gelöscht. Eine WHERE-Klausel wird jedoch nicht verwendet.|  
|**pubid**|**uniqueidentifier**|Der eindeutige Bezeichner der Veröffentlichung.|  
|**status**|**tinyint**|Gibt den Status des Artikels vom Typ schema only an, der einen der folgenden Werte annehmen kann:<br /><br /> **1** = unsynchronisiert - das Anfangsverarbeitungsskript der Tabelle ausgeführt, das nächste Mal Veröffentlichen der Momentaufnahme-Agent ausgeführt wird.<br /><br /> **2** = aktiv - das Anfangsverarbeitungsskript zum Veröffentlichen der Tabelle ausgeführt wurde.<br /><br /> **5** = New_inactive - hinzugefügt werden.<br /><br /> **6** = New_active - hinzugefügt werden.|  
|**creation_script**|**nvarchar(255)**|Der Pfad und Name eines optionalen Artikel-Schemavorabskripts, mit dem die Zieltabelle erstellt wird.|  
|**schema_option**|**binary(8)**|Das Bitmuster der Option zur Schemaerstellung für den angegebenen Artikel vom Typ schema only, das das bitweise logische OR-Ergebnis von mindestens einer dieser Werte sein kann:<br /><br /> **0 x 00** = deaktiviert die Skripterstellung durch den Momentaufnahme-Agent und verwendet das bereitgestellte Skript CreationScript.<br /><br /> **0 x 01** = generiert die objekterstellung (CREATE TABLE, CREATE PROCEDURE usw.).<br /><br /> **0 x 10** = generiert einen entsprechenden gruppierten Index.<br /><br /> **0 x 20** = konvertiert benutzerdefinierte Datentypen, um Datentypen in Basisdatentypen.<br /><br /> **0 x 40** = generiert entsprechende(n) nicht gruppierte(n) Index bzw. Indizes.<br /><br /> **0 x 80** = enthält die deklarierte referenziellen Integrität für die Primärschlüssel.<br /><br /> **0 x 100** = repliziert Benutzertrigger für einen Tabellenartikel, falls definiert.<br /><br /> **0 x 200** = repliziert foreign Key-Einschränkungen. Wenn die Tabelle, auf die verwiesen wird, nicht Teil einer Veröffentlichung ist, werden keine Fremdschlüsseleinschränkungen für eine veröffentlichte Tabelle repliziert.<br /><br /> **0 x 400** = repliziert Check-Einschränkungen.<br /><br /> **0 x 800** = repliziert Standardwerte.<br /><br /> **0 x 1000** = replizieren spaltensortierung.<br /><br /> **0 x 2000** = repliziert erweiterte Eigenschaften, die das Quellobjekt des veröffentlichten Artikels zugeordnet.<br /><br /> **0 x 4000** = repliziert eindeutige Schlüssel, wenn für einen Tabellenartikel definiert.<br /><br /> **0 x 8000** = repliziert einen Primärschlüssel und eindeutige Schlüssel für eine Tabelle Artikel als Einschränkungen mithilfe von ALTER TABLE-Anweisungen.<br /><br /> Weitere Informationen zu den möglichen Werten für **Schema_option**, finden Sie unter [Sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**destination_object**|**sysname**|Der Name des Zielobjekts in der Abonnementdatenbank. Dieser Wert gilt nur für Artikel vom Typ schema only, wie z. B. gespeicherte Prozeduren, Sichten und UDFs.|  
|**destination_owner**|**sysname**|Der Besitzer des Objekts in der Abonnementdatenbank, wenn er nicht ist **Dbo**.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
