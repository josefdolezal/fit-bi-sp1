# Model tříd

## Manager
Tato komponenta zodpovídá za komunikaci mezi produkční databází a komponentami,
které k ní nemají přístup (DataProvider a Finder). Manager plánuje práci pro
DataProvidera, kterému předává seznam produktů ke zjištění cen.
Tento seznam také obsahuje URL, na kterých se produkt nalézá, šablonu parsování
a nastavení proxy. Manager také připravuje seznam nových produktů pro Findera,
který následně vrátí množinu URL, na kterých se produkt nachází. Tato komponenta
je zodpovědná za vkládání zjištěných dat do produkční databáze. V případě
vyskytnutí chyb dokáže Manager chyby vyřešit automaticky, nebo je předat
komponentě Front-end, která nechá chybu vyřešit správcem systému.

## Třídy

```
Shared +
Local -

|+ Template
   |priva productId : Int
   |priva priceSelector : String
   |priva priceVatSelector : String

|+ Proxy
   |priva proxyId : Int
   |priva serverAddress : String
   |priva port : String
   |priva username : String
   |priva password : String

|+ Records
   |priva date : DateTime
   |priva price : Double
   |priva priceVat : Double

|+ DataRequest
   |priva product : Product
   |priva dataHistory : Records
   |priva siteUrl : String
   |priva proxy : Proxy
   |priva template : ParserTemplate

|+ Product
   |priva internalID : Int
   |priva name : String
   |priva lastUpdateAttempt : DateTime

|- Manager
|- (Abstract) JobPlanner
   |- (Extends) ProductFinder
      |- pubm init(product: Product)

   |- (Extends) ProductUpdater

|- ProxyAllocator
   |pubm_s AvailableProxy(forUrl: String) -> Proxy
      |throws NoProxyAvailableException

```
