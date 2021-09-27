# Tao bang product-manager

* Chui vào MySql container.

        docker exec -it learn-mysql /bin/bash
        mysql -u <username> -p<password>

* Tạo database.

    CREATECREATE DATABASE product_management;

    ![login-create-database](https://github.com/vudt0911/Database/blob/main/HomeWork1/screenshots/login-create-database.png)

* Tạo bảng product với các cột mã sản phẩm, tên sản phẩm, loại sản phẩm (thực phẩm, đồ gia dụng, đồ điện tử, ...) số lượng, số lượng bán, giá bán, ngày sản xuất, hạn sử dụng.

        mysql> USE product_management
        Database changed
        mysql> CREATE TABLE product (
        -> id INT unsigned PRIMARY KEY AUTO_INCREMENT,
        -> name VARCHAR(150) NOT NULL,
        -> category ENUM('THUC PHAM', 'DO GIA DUNG','DO DIEN TU') NOT NULL,
        -> amount INT unsigned NOT NULL,
        -> amount_sell INT unsigned NOT NULL,
        -> price BIGINT unsigned NOT NULL,
        -> date_of_manufacture DATE NOT NULL,
        -> expiry_date DATE NOT NULL
        -> );
    Query OK, 0 rows affected (0.03 sec)

![create-table](https://github.com/vudt0911/Database/blob/main/HomeWork1/screenshots/create-table.png)

* Show table

![show-table](https://github.com/vudt0911/Database/blob/main/HomeWork1/screenshots/show-table.png)

* Thêm sản phẩm vào bảng vừa tạo.

    mysql> INSERT INTO product (id, name, category, amount, amount_sell, price, date_of_manufacture, expiry_date)
        ->  VALUES (1, 'Tao', 'THUC PHAM', 2000, 1000, 15000, '2021-09-03', '2021-09-27'),
        -> (2, 'Cam', 'THUC PHAM', 2500, 1300, 25000, '2021-09-17', '2021-10-03'),
        -> (3, 'Quat', 'DO GIA DUNG', 200, 150, 350000, '2021-08-01', '2022-08-01'),
        -> (4, 'Dien Thoai', 'DO DIEN TU', 1500, 1000, 7950000, '2020-09-27', '2021-09-27'),
        -> (5, 'Lap Top', 'DO DIEN TU', 200, 90, 15000000, '2020-07-03', '2021-03-07');
    Query OK, 5 rows affected (0.01 sec)
    Records: 5  Duplicates: 0  Warnings: 0

![insert-data](https://github.com/vudt0911/Database/blob/main/HomeWork1/screenshots/insert-data.png)


