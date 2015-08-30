Rails-way
=========

## Work with NOSQL

* [以序列化方式儲存document](https://github.com/kevin-shu/Rails-way/wiki/%E4%BB%A5%E5%BA%8F%E5%88%97%E5%8C%96%E6%96%B9%E5%BC%8F%E5%84%B2%E5%AD%98document)
* [將SQL中的資料sync到ElasticSearch增進搜尋效能](https://github.com/kevin-shu/Rails-way/wiki/%E5%B0%87SQL%E4%B8%AD%E7%9A%84%E8%B3%87%E6%96%99sync%E5%88%B0ElasticSearch%E5%A2%9E%E9%80%B2%E6%90%9C%E5%B0%8B%E6%95%88%E8%83%BD)

## ActiveRecord

## Background-job
最常見的是"delayed_job"、"sidekiq"、"resque"，大致可分為使用「sql」或「redis」來存que兩種。  

### delayed_job
首先簡稱"DJ"的delayed_job是使用SQL來儲存que，好處是設定方便，不用另外裝redis。安裝方法：

1. 在Gemfile中加入'delayed_job_active_record', 'delayed_job', 'daemons', 然後 `bundle install`
2. run `rails generate delayed_job:active_record`，產生存que的table，並`rake db:migrate`

安裝完以後千萬要記得啟動他才有用啊：
```
RAILS_ENV=production script/delayed_job -n (worker數目) start|restart|stop
```
  
### resque, sidekiq
至於"sidekiq"和"resque"都是使用sidekiq做que的管理，performance會比用SQL好，但要多裝一個redis，也相對麻煩一點。  
他們兩者的差別在於resque是single-threaded、sidekiq是multi-threaded。也就是當要平行執行n個task時，resque也必須開啟n個process才行，相較之下sidekiq所佔用的memory就較少。  
可以姑且把sidekiq想成是resque的進化版。如何安裝和使用就不多做介紹了。


## Cache

* [Page Caching](https://github.com/kevin-shu/Rails-way/wiki/Page-cache)
* [Fragment Caching](https://github.com/kevin-shu/Rails-way/wiki/Fragment-Caching)
* [SQL Cache](https://github.com/kevin-shu/Rails-way/wiki/SQL-cache)


## 環境設定
* [figaro](https://github.com/laserlemon/figaro) - 比SettingsLogic好用一點


## Useful gems

* Tire(https://github.com/karmi/tire)
* Oj(https://github.com/ohler55/oj)
* Better Errors(https://github.com/charliesome/better_errors)
* miniprofiler(https://github.com/harleyttd/miniprofiler)
* Settingslogic(https://github.com/binarylogic/settingslogic)
* Brakeman(https://github.com/presidentbeef/brakeman)
* Whenever(https://github.com/javan/whenever)
