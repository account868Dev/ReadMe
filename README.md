## 고치고 싶은곳은 언제든 수정~
## 개발할 서버목록

## 1. 계정 서버
#####  - 유저 계정 관리
#####  - 유저 로그인 및 회원가입
  
## 2. 음식점 추천 및 리스트 서버
#####  - 음식점 추천 및 리스트 제공
#####  - 음식점 검색

## 3. 배치 서버
#####  - 구글 PlaceAPI 
#####  - 기타

## DB스키마

<pre><code>
CREATE TABLE `location_codes` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `parent_id` int(11) DEFAULT NULL,
  `type` char(2) DEFAULT NULL,
  `city_name` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


CREATE TABLE `restaurant_contents` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `restaurant_id` int(11) DEFAULT NULL,
  `order` int(11) DEFAULT NULL,
  `type` varchar(2) DEFAULT NULL,
  `use_yn` int(1) DEFAULT NULL,
  `image_name` varchar(50) DEFAULT NULL,
  `image_url` varchar(200) DEFAULT NULL,
  `contents` varchar(500) DEFAULT NULL,
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


CREATE TABLE `restaurants` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `location_code` int(11) DEFAULT NULL,
  `name` varchar(20) DEFAULT NULL,
  `use_yn` char(1) DEFAULT NULL,
  `address` varchar(200) DEFAULT NULL,
  `address2` varchar(200) DEFAULT NULL,
  `zip_code` varchar(50) DEFAULT NULL,
  `phone_number` varchar(20) DEFAULT NULL,
  `latitude` float DEFAULT NULL,
  `longtitude` float DEFAULT NULL,
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


CREATE TABLE `reviews` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `restaurantId` int(11) DEFAULT NULL,
  `user_id` int(11) DEFAULT NULL,
  `grade` int(11) DEFAULT NULL,
  `contents` varchar(500) DEFAULT NULL,
  `use_yn` char(1) DEFAULT NULL,
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


CREATE TABLE `user_histories` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `rank` int(11) DEFAULT NULL,
  `restaurant_id` int(11) DEFAULT NULL,
  `user_id` int(11) DEFAULT NULL,
  `weather_id` int(11) DEFAULT NULL,
  `crated_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


CREATE TABLE `users` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `email` varchar(50) DEFAULT NULL,
  `name` varchar(50) DEFAULT NULL,
  `use_yn` char(1) DEFAULT NULL,
  `sns_yn` char(1) DEFAULT NULL,
  `recomended_use_yn` char(1) DEFAULT NULL,
  `recomended_time` int(11) DEFAULT NULL,
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

</code></pre>
