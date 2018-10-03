---
title: DMSCHEMA_MINING_SERVICES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_SERVICES
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICES rowset
ms.assetid: 4a672f2f-d637-4def-a572-c18556f83d34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba6a0172207c84bb2bdb4b7e3de7acc84362b8f7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099761"
---
# <a name="dmschemaminingservices-rowset"></a>DMSCHEMA_MINING_SERVICES-Rowset
  Stellt eine Beschreibung jedes Data Mining-Algorithmus bereit, den der Anbieter unterstützt.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_SERVICES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Name des Algorithmus Diese Spalte ist anbieterspezifisch.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`||Diese Spalte enthält eine Bitmap, die den Miningdienst beschreibt. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] füllt diese Spalte mit einem der folgenden Werte an:<br /><br /> -   `DM_SERVICETYPE_CLASSIFICATION` (`1`)<br />-   `DM_SERVICETYPE_CLUSTERING` (`2`)|  
|`SERVICE_DISPLAY_NAME`|`DBTYPE_WSTR`||Ein lokalisierbarer Anzeigename für den Algorithmus.|  
|`SERVICE_GUID`|`DBTYPE_GUID`||Der GUID für den Algorithmus.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung des Algorithmus.|  
|`PREDICTION_LIMIT`|`DBTYPE_UI4`||Die maximale Anzahl der Vorhersagen, die von dem Modell und dem Algorithmus bereitgestellt werden können.|  
|`SUPPORTED_DISTRIBUTION_FLAGS`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Flags, die die statistischen Verteilungen beschreibt, die vom Algorithmus unterstützt werden. Diese Spalte enthält mindestens einen der folgenden Werte:<br /><br /> -   "`NORMAL`"<br />-   "`LOG NORMAL`"<br />-   "`UNIFORM`"|  
|`SUPPORTED_INPUT_CONTENT_TYPES`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Flags, die die Eingabeinhaltstypen beschreibt, die vom Algorithmus unterstützt werden. Diese Spalte enthält mindestens einen der folgenden Werte:<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-   "`DISCRETIZED`"<br />-   "`ORDERED`"<br />-"SCHLÜSSEL `SEQUENCE`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY VARIANCE`"<br />-   "`PROBABILITY STDEV`"<br />-   "`KEY TIME`"|  
|`SUPPORTED_PREDICTION_CONTENT_TYPES`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste von Flags, die die Vorhersageinhaltstypen beschreibt, die vom Algorithmus unterstützt werden. Diese Spalte enthält mindestens einen der folgenden Werte:<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-   "`DISCRETIZED`"<br />-   "`ORDERED`"<br />-"SCHLÜSSEL `SEQUENCE` "<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY VARIANCE`"<br />-   "`PROBABILITY STDEV`"<br />-"KEY TIME"|  
|`SUPPORTED_MODELING_FLAGS`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste der Modellierungsflags, die vom Algorithmus unterstützt werden. Diese Spalte enthält mindestens einen der folgenden Werte:<br /><br /> -   "`MODEL_EXISTENCE_ONLY`"<br />-   "`REGRESSOR`"<br /><br /> Es können auch anbieterspezifische Flags definiert werden.|  
|`SUPPORTED_SOURCE_QUERY`|`DBTYPE_WSTR`||– Diese Spalte wird für die Abwärtskompatibilität unterstützt.|  
|`TRAINING_COMPLEXITY`|`DBTYPE_I4`||Die Zeitpanne, die das Training voraussichtlich dauern wird:<br /><br /> -   `DM_TRAINING_COMPLEXITY_LOW` Gibt an, dass die Ausführungszeit relativ kurz und proportional zur Eingabe.<br />-   **DM_TRAINING_COMPLEXITY_MEDIUM** gibt an, dass die Ausführungszeit länger sein kann, aber es im Allgemeinen proportional zur Eingabe ist.<br />-   **DM_TRAINING_COMPLEXITY_HIGH** gibt an, dass die Ausführungszeit lang ist und es in Beziehung zu die Anzahl der Trainingsfälle exponentiell kann.|  
|`PREDICTION_COMPLEXITY`|`DBTYPE_I4`||Die Zeitpanne, die die Vorhersage voraussichtlich dauern wird:<br /><br /> -   **DM_PREDICTION_COMPLEXITY_LOW** gibt an, dass die Ausführungszeit relativ kurz und proportional zur Eingabe.<br />-   **DM_PREDICTION_COMPLEXITY_MEDIUM** gibt an, dass die Ausführungszeit länger sein kann, aber es im Allgemeinen proportional zur Eingabe ist.<br />-   **DM_PREDICTION_COMPLEXITY_HIGH** gibt an, dass die Ausführungszeit lang ist und es in Beziehung zu die Anzahl der Trainingsfälle exponentiell kann.|  
|`EXPECTED_QUALITY`|`DBTYPE_I4`||Die erwartete Qualität des mit diesem Algorithmus erstellten Modells:<br /><br /> -   `DM_EXPECTED_QUALITY_LOW`<br />-   `DM_EXPECTED_QUALITY_MEDIUM`<br />-   **DM_EXPECTED_QUALITY_HIGH**|  
|`SCALING`|`DBTYPE_I4`||Die Skalierbarkeit des Algorithmus:<br /><br /> -   **DM_SCALING_LOW**<br />-   `DM_SCALING_MEDIUM`<br />-   **DM_SCALING_HIGH**|  
|`ALLOW_INCREMENTAL_INSERT`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob der Algorithmus inkrementelles Training unterstützt, d. h. das Aktualisieren der erkannten Muster auf der Grundlage der neuen tatsächlichen Daten, anstatt die Muster vollständig neu zu erkennen.|  
|`ALLOW_PMML_INITIALIZATION`|`DBTYPE_BOOL`||Ein boolescher Wert, der anzeigt, ob Miningmodelle auf der Grundlage einer PMML 2.1-Zeichenfolge erstellt werden können.<br /><br /> Wenn auf `TRUE` festgelegt, unterstützt der Algorithmus die Initialisierung von PMML 2.1-Inhalten.|  
|`CONTROL`|`DBTYPE_I4`||Die vom Dienst bereitgestellte Unterstützung, wenn das Training unterbrochen wird:<br /><br /> -   `DM_CONTROL_NONE` Gibt an, dass der Algorithmus nicht abgebrochen werden kann, nach dem Start zum Trainieren des Modells.<br />-   `DM_CONTROL_CANCEL` Gibt an, dass der Algorithmus abgebrochen werden kann, nachdem es beginnt, die zum Trainieren des Modells und neu gestartet werden, muss um das Training fortzusetzen.<br />-   `DM_CONTROL_SUSPENDRESUME` Gibt an, dass der Algorithmus abgebrochen und zu einem beliebigen Zeitpunkt fortgesetzt werden kann, aber auf die Ergebnisse nicht verfügbar, sind bis die Schulung abgeschlossen ist.<br />-   `DM_CONTROL_SUSPENDWITHRESULT` Gibt an, dass der Algorithmus abgebrochen und zu einem beliebigen Zeitpunkt fortgesetzt werden kann, und alle inkrementellen Ergebnisse abgerufen werden können.|  
|`ALLOW_DUPLICATE_KEY`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob Fälle doppelte Schlüssel enthalten können.<br /><br /> Wenn `VARIANT_TRUE` festgelegt ist, können Fälle doppelte Schlüssel enthalten.|  
|`VIEWER_TYPE`|`DBTYPE_WSTR`||Der empfohlene Viewer für dieses Modell.|  
|`HELP_FILE`|`DBTYPE_WSTR`||(Optional) Der Name der Datei, die die Dokumentation für diesen Dienst enthält.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||(Optional) Die Hilfekontext-ID für diesen Dienst.|  
|`MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL`|`DBTYPE_WSTR`||Die unterstützte DDL-Version. 0 gibt an, dass DDL nicht unterstützt wird.|  
|`MSOLAP_SUPPORTS_OLAP_MINING_MODELS`|`DBTYPE_BOOL`||Ein boolescher Wert, der anzeigt, ob OLAP-Miningmodelle erstellt werden können.<br /><br /> Wenn `TRUE` festgelegt ist, können OLAP-Miningmodelle erstellt werden. Dafür darf `MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL` nicht null sein.|  
|`MSOLAP_SUPPORTS_DATA_MINING_DIMENSIONS`|`DBTYPE_BOOL`||Ein boolescher Wert, der anzeigt, ob Data Mining-Dimensionen erstellt werden können.<br /><br /> Wenn `TRUE` festgelegt ist, können Miningdimensionen erstellt werden.|  
|`MSOLAP_SUPPORTS_DRILLTHROUGH`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob der Dienst Drillthroughfunktionen unterstützt.<br /><br /> Wenn `TRUE` festgelegt ist, unterstützt der Dienst Drillthroughfunktionen.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DMSCHEMA_MINING_SERVICES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
