# countries-states-councils
A SQL file with countres (multilanguage), states/regions and councils with geolocation

# Schema
```sql
CREATE TABLE `language` (
  `id` tinyint(2) unsigned NOT NULL AUTO_INCREMENT,
  `code` varchar(10) DEFAULT NULL,
  `status` tinyint(1) unsigned NOT NULL DEFAULT '1',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

CREATE TABLE `country` (
  `id` smallint(6) unsigned NOT NULL AUTO_INCREMENT,
  `id_language` tinyint(2) unsigned NOT NULL DEFAULT '0',
  `name` varchar(150) DEFAULT NULL,
  `x` float(13,10) NOT NULL DEFAULT '0.0000000000',
  `y` float(13,10) NOT NULL DEFAULT '0.0000000000',
  PRIMARY KEY (`id`,`id_language`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

CREATE TABLE `state` (
  `id` smallint(6) unsigned NOT NULL AUTO_INCREMENT,
  `id_country` smallint(6) unsigned NOT NULL DEFAULT '0',
  `id_language` tinyint(2) unsigned NOT NULL DEFAULT '0',
  `name` varchar(150) DEFAULT NULL,
  `x` float(13,10) NOT NULL DEFAULT '0.0000000000',
  `y` float(13,10) NOT NULL DEFAULT '0.0000000000',
  `exact` tinyint(1) NOT NULL DEFAULT '0',
  PRIMARY KEY (`id`,`id_country`,`id_language`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

CREATE TABLE `council` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `id_state` smallint(6) unsigned NOT NULL DEFAULT '0',
  `id_country` smallint(6) unsigned NOT NULL DEFAULT '0',
  `id_language` tinyint(2) unsigned NOT NULL DEFAULT '0',
  `name` varchar(150) DEFAULT NULL,
  `x` float(13,10) NOT NULL DEFAULT '0.0000000000',
  `y` float(13,10) NOT NULL DEFAULT '0.0000000000',
  `exact` tinyint(1) NOT NULL DEFAULT '0',
  PRIMARY KEY (`id`,`id_state`,`id_country`,`id_language`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
