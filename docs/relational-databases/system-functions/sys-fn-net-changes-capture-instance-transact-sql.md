---
title: sys. fn_net_changes_&lt;capture_instance&gt; (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_net_changes_TSQL
- fn_net_changes_TSQL
- fn_net_changes
- sys.fn_net_changes
dev_langs:
- TSQL
helpviewer_keywords:
- fn_net_changes_<capture_instance>
- sys.fn_net_changes_<capture_instance>
ms.assetid: 342fa030-9fd9-4b74-ae4d-49f6038a5073
author: rothja
ms.author: jroth
ms.openlocfilehash: 556518a5fc2950ff69e6a872df5387b4c8367c6b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68122567"
---
# <a name="sysfn_net_changes_ltcapture_instancegt-transact-sql"></a>sys. fn_net_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wrapper für die Abfragefunktionen der **net-Änderungen** . Die zum Erstellen dieser Funktionen erforderlichen Skripts werden von der gespeicherten Prozedur sys.sp_cdc_generate_wrapper_function generiert.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_net_changes_<capture_instance> ('start_time', 'end_time', '<row_filter_option>' )  
  
<capture_instance> ::= The name of the capture instance.  
<row_filter_option> ::=  
{ all  
  | all with mask  
  | all with merge  
}  
```  
  
## <a name="arguments"></a>Argumente  
 *start_time*  
 Der **DateTime** -Wert, der den unteren Endpunkt des Bereichs von Änderungs Tabellen Einträgen darstellt, der im Resultset enthalten sein soll.  
  
 Im Resultset sind nur Zeilen in der CDC. <capture_instance>_CT Änderungs Tabelle enthalten, denen eine comdtzeit zugeordnet ist, die streng größer als *start_time* ist.  
  
 Wenn für dieses Argument ein Wert von NULL übergeben wird, entspricht der untere Endpunkt des Abfragebereichs dem unteren Endpunkt des gültigen Bereichs der Aufzeichnungsinstanz.  
  
 *end_time*  
 Der **DateTime** -Wert, der den hohen Endpunkt des Bereichs von Änderungs Tabellen Einträgen darstellt, der im Resultset enthalten sein soll.  
  
 Dieser Parameter kann eine der beiden Bedeutungen annehmen, abhängig von dem für @closed_high_end_point ausgewählten Wert, wenn sys. sp_cdc_generate_wrapper_function aufgerufen wird, um das Skript zum Erstellen der Wrapper Funktion zu generieren:  
  
-   @closed_high_end_point = 1  
  
     Im Resultset sind nur Zeilen in der Tabelle cdc. <capture_instance>_CT Änderungs \_ \_Tabelle enthalten, die einen Wert in $Start _lsn und eine entsprechende comdzeit aufweisen, die kleiner oder gleich **start_time** ist.  
  
-   @closed_high_end_point = 0  
  
     Im Resultset sind nur Zeilen in der CDC. <capture_instance>_CT Änderungs Tabelle \_ \_enthalten, die einen Wert in $Start _lsn und eine entsprechende comdtzeit aufweisen, die streng kleiner als **start_time** ist.  
  
 Wenn für dieses Argument ein Wert von NULL übergeben wird, entspricht der obere Endpunkt des Abfragebereichs dem oberen Endpunkt des gültigen Bereichs der Aufzeichnungsinstanz.  
  
 *<row_filter_option>* :: = {all | all with mask | all with Merge}  
 Eine Option, die den Inhalt der Metadatenspalten sowie die im Resultset zurückgegebenen Zeilen bestimmt. Eine der folgenden Optionen ist möglich:  
  
 all  
 Gibt den endgültigen Inhalt einer geänderten Zeile in den Inhaltsspalten zurück sowie den erforderlichen Vorgang zum Anwenden der Zeile in der Metadatenspalte __CDC_OPERATION.  
  
 all with mask  
 Gibt den endgültigen Inhalt einer geänderten Zeile in den Inhaltsspalten zurück sowie den erforderlichen Vorgang zum Anwenden der einzelnen Zeilen in der Metadatenspalte __CDC_OPERATION. Wenn bei Generierung des Skripts zur Erstellung der Wrapperfunktion eine Aktualisierungsflagliste angegeben wurde, müssen Sie mit dieser Option die Aktualisierungsmaske füllen.  
  
 all with merge  
 Gibt den endgültigen Inhalt aller in den Inhaltsspalten geänderten Zeilen zurück.  
  
 Der Spalten __CDC_OPERATION ist einer der folgenden beiden Werte:  
  
-   D, wenn die Zeile gelöscht werden muss  
  
-   M, wenn die Zeile eingefügt oder aktualisiert werden muss  
  
 Die Logik zum Bestimmen, ob eine Einfügung oder eine Aktualisierung erforderlich ist, um eine Änderung auf ein Ziel anzuwenden, führt zu mehr Komplexität bei der Abfrage. Verwenden Sie diese Option für verbesserte Leistung, wenn nicht zwischen Einfügungs- und Aktualisierungsvorgängen unterschieden werden muss. Dieser Ansatz eignet sich besonders für Zielumgebungen, in denen Mergevorgänge direkt verfügbar sind, z. B. in einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Umgebung.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Spaltentyp|Beschreibung|  
|-----------------|-----------------|-----------------|  
|\<Spalten aus @column_list>|**variiert**|Die Spalten, die im **column_list** -Argument für die sp_cdc_generate_wrapper_function identifiziert werden, wenn Sie aufgerufen wird, um das Skript zum Erstellen des Wrappers zu generieren. Wenn *column_list* NULL ist, werden alle nach verfolgten Quell Spalten im Resultset angezeigt.|  
|__CDC_OPERATION|**nvarchar (2)**|Ein Vorgangscode, der angibt, welcher Vorgang auf die Zeile der Zielumgebung angewendet werden muss. Der Vorgang variiert basierend auf dem Wert des Argument *row_filter_option* , das im folgenden-Befehl bereitgestellt wird:<br /><br /> *row_filter_option* = ' all ', ' all with mask '<br /><br /> 'D' - Löschvorgang<br /><br /> 'I' - Einfügevorgang<br /><br /> 'UN' - Aktualisierungsvorgang<br /><br /> *row_filter_option* = ' all with merge '<br /><br /> 'D' - Löschvorgang<br /><br /> 'M' - Einfüge- oder Aktualisierungsvorgang|  
|\<Spalten aus @update_flag_list>|**bit**|Ein Bitflag, das durch Anhängen von _uflag an den Spaltennamen benannt wird. Das Flag nimmt nur dann einen Wert ungleich NULL an, wenn *row_filter_option* **= ' all with mask '** und \__CDC_OPERATION **= ' un '**. Es wird auf 1 eingestellt, wenn die entsprechende Spalte innerhalb des Abfragefensters geändert wurde. Andernfalls ist es 0.|  
  
## <a name="remarks"></a>Hinweise  
 Die fn_net_changes_<capture_instance> Funktion dient als Wrapper für die Abfragefunktion CDC. fn_cdc_get_net_changes_<capture_instance>. Die gespeicherte Prozedur sys. sp_cdc_generate_wrapper wird zum Erstellen des Skripts für den Wrapper verwendet.  
  
 Wrapperfunktionen werden nicht automatisch erstellt. Es gibt zwei Dinge, die Sie tun müssen, um Wrapper Funktionen zu erstellen:  
  
1.  Führen Sie die gespeicherte Prozedur aus, um das Skript zu generieren, das den Wrapper erstellt.  
  
2.  Führen Sie das Skript aus, das die Wrapperfunktion tatsächlich erstellt.  
  
 Wrapper Funktionen ermöglichen Benutzern eine systematische Abfrage von Änderungen, die in einem Intervall aufgetreten sind, das durch **DateTime** -Werte und nicht durch LSN-Werte begrenzt ist. Die Wrapper Funktionen führen alle erforderlichen Konvertierungen zwischen den angegebenen **DateTime** -Werten und den LSN-Werten aus, die intern als Argumente für die Abfragefunktionen erforderlich sind. Wenn die Wrapper Funktionen serialisiert zum Verarbeiten eines Streams von Änderungs Daten verwendet werden, stellen Sie sicher, dass keine Daten verloren gehen oder wiederholt werden, sofern die folgende Konvention @end_time befolgt wird: der Wert des Intervalls, das einem- @start_time Befehl zugeordnet ist, wird als Wert für das Intervall angegeben, das dem nachfolgenden-Befehl zugeordnet ist.  
  
 Wenn Sie den Parameter @closed_high_end_point bei Erstellung des Skripts verwenden, können Sie Wrapper generieren, die im angegebenen Abfragefenster eine geschlossene obere Grenze oder eine offene untere Grenze unterstützen. Sie können also entscheiden, ob Einträge mit einer Commitzeit in das Intervall aufgenommen werden sollen, die der oberen Grenze des Extrahierungsintervalls entspricht. Standardmäßig wird die Obergrenze aufgenommen.  
  
 Das Resultset, das von der **net Changes** -Wrapper Funktion zurückgegeben wird, gibt nur die nach @column_list verfolgten Spalten zurück, die beim Generieren des Wrappers in der waren. Wenn @column_list NULL ist, werden alle verfolgten Quellspalten zurückgegeben. Den Quellspalten folgt die Vorgangspalte, __CDC_OPERATION. Es handelt sich um eine Spalte mit einem oder zwei Zeichen, die den Vorgang identifiziert.  
  
 Bitflags werden dann an das Resultset für jede Spalte angehängt, die im-Parameter @update_flag_listidentifiziert wird. Für den **net Changes** -Wrapper sind die Bitflags immer NULL, wenn der @row_filter_option im Aufrufder Wrapper Funktion verwendete ' all ' oder ' all with merge ' ist. Der Wert des Flags ist ebenfalls NULL, wenn die @row_filter_option auf 'all with mask' und __CDC_OPERATION auf 'D' oder 'I' gesetzt ist. Wenn \__CDC_OPERATION auf ' un ' festgelegt ist, wird das Flag auf 1 oder 0 festgelegt, je nachdem, ob der **net** Update-Vorgang eine Änderung an der Spalte verursacht hat.  
  
 Die Change Data Capture Konfigurations Vorlage ' Instantiate CDC Wrapper TVFs for Schema ' zeigt, wie die gespeicherte Prozedur sp_cdc_generate_wrapper_function verwendet wird, um CREATE-Skripts für alle Wrapper Funktionen für die definierten Abfragefunktionen eines Schemas abzurufen. Diese Skripts werden dann von der Vorlage erstellt. Weitere Informationen zu Vorlagen finden Sie unter [Vorlagen-Explorer](../../ssms/template/template-explorer.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. sp_cdc_generate_wrapper_function &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)  
  
  
