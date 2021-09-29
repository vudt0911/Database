# Câu hỏi:
Sử dụng database sakila, thực hiện các câu truy vấn sau:

1, Lấy tên phim, rating, special_features các bộ phim có rating là NC-17 hoặc R, có special_features là Trailers

2, Lấy ra tên phim, length các bộ phim có length nhỏ hơn 70 hoặc length lớn hơn 100. Sắp xếp phim theo thứ tự length tăng dần

3, Lấy ra các actor có first_name bắt đầu là chữ B và sắp xếp theo thứ tự last_name tăng dần

4, Lấy ra các bộ phim không có chứa từ 'LIFE', không phải rating PG và sắp xếp theo thứ tự length giảm dần

# Lấy tên phim, rating, special_features các bộ phim có rating là NC-17 hoặc R, có special_features là Trailers

* lấy tên phim, rating, special_feature -> SELECT title, rating, special_feature

* vì là fiml nên sẽ lấy trong bảng film -> FROM film

* bộ phim có rating là NC_17 hoặc R ->rating IN('NC-17', 'R')

* có special_features là Trailers. Vì câu hỏi là có chứ không phải là chứa, bắt đầu bằng, kết thúc bằng... nên trong phần này có thể dùng special_features = 'Trailers'  hoặc  special_features LIKE 'Trailers' đều cho ra 1 kết quả 

Code tổng thể

    SELECT title, rating, special_features
    FROM `film`
    WHERE (rating IN('NC-17', 'R') AND special_features LIKE 'Trailers') 

hoặc 
    
        SELECT title, rating, special_features
        FROM `film`
        WHERE (rating IN('NC-17', 'R') AND special_features = 'Trailers')
    

![code](/image/1-1.png)
![code](/image/1-2.png)
![code](/image/1-3.png)

# Lấy ra tên phim, length các bộ phim có length nhỏ hơn 70 hoặc length lớn hơn 100. Sắp xếp phim theo thứ tự length tăng dần

cách 1: 

    SELECT title, length
    FROM `film`
    WHERE length NOT BETWEEN 70 AND 100
    ORDER BY length ASC

cách 2:

    SELECT title, length
    FROM `film`
    WHERE length < 70 OR length > 100
    ORDER BY length ASC

![code](/image/2-1.png) 
![code](/image/2-2.png) 

# Lấy ra các actor có first_name bắt đầu là chữ B và sắp xếp theo thứ tự last_name tăng dần

    SELECT first_name, last_name
    FROM `actor` 
    WHERE first_name LIKE 'B%'
    ORDER BY last_name ASC

![code](/image/3-1.png) 
![code](/image/3-2.png) 

# Lấy ra các bộ phim không có chứa từ 'LIFE', không phải rating PG và sắp xếp theo thứ tự length giảm dần

    SELECT title, rating
    FROM `film` 
    WHERE title NOT LIKE '%LIFE%' AND rating != 'PG'
    ORDER BY length DESC

![code](/image/4-1.png) 
![code](/image/4-2.png) 
