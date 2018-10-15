DEMO: WLP + MySQL + wlpJdbcSample aplikacija na OpenShift V3.9
==============================================================
http://wlp-centos-http-route-myproject.192.168.99.100.nip.io/wlpJdbcSample/HelloWorld

A. Sažetak
===========

Napravljen je demo koji prikazuje build-anje aplikacijskog image-a unutar Openshift okoline 
korištenjem Dockerfile strategije gdje se većina potrebnih artefakata dohvaća iz Github repozitorija.
Preduvijeti:
* u lokalni Openshift Docker registry je stavljen wlp base image (pull-anjem iz DockeHub-a ili lokalnim buildanjem)
* pripremljena je instanca MySLQ poslužitelja sa "testdb" bazom podataka (kao kontejner napravljen na temelju standardnog 
  MySQL image-a sa persistent storage-om)
* kreiran je configMap objekt koji sadrži podatke "server.env" datoteke za demo okolinu (sadrži WLP i MySQL podatke)
* kreirati u lokalnom Openshift registry-u repo naziva "wlp-centos"

B. Koraci kod uspostave demo-a
==============================

1. Kreiranje aplikacijskog image-a
----------------------------------

* Pokrenuti build aplikacijskog image-a korištenjem pripremljenog BuildConfig objekta. 
  (wlp-centos-buildconfig.yaml).
  Build koristi Dockerfile strategiju i dohvaća potrebne artefakte sa Github repozitorija 
  (https://github.com/dsamec3/dudo-samples.git, "websphere-liberty" direktorij).
  Kao rezultat build-a kreira se image u lokalnom OpenShift registry-u u repozitoriju "wlp-centos"
* Pokrenuti deploy aplikacijskog kontejnera korištenjem pripremljenog DeploymentConfig objekta
  (wlp-centos-deployconfig.yaml).
  Da bi se ispravno pokrenuo WLP i aplikacija mogla pristupiti "testdb" bazi podataka potrebno je u 
  Deployconfig objektu mount-ati "server.env" datoteku korištenjem 
* 

