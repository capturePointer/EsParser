# EsParser
php的操作类库，通过写sql来转化dsl来查询elasticsearch
### 使用方法
    require_once dirname(__FILE__) . '/lib/EsParser.php';
    //$sql = 'select a.*,count(a.id) as id,sum(a.price) as total_price,sum(a.total) as count_total from table1 a where a.a=12 and a.b=36 and a.c like "%5%" and a.d>=10 and a.d<20 and a.h>56 and a.f in(1,2,3,4,5) group by a.name order by a.id desc limit 10';
    //$sql='select a.*,count(a.id) as sid,a.total_price,sum(a.total) as count_total from table1 group by a.total_price order by count_total,a.co';
    //$sql = 'select * from alp_dish_sales_saas where sid in(994,290) limit 0,10';
    $sql='select category_name cate_name,dish_name,dishsno,sale_date,sum(total_price) total_price,sum(total_count) total_count,category_name,sku_name properties from alp_dish_sales_saas 
				where sale_date>="2017-01-01" and sale_date<="2017-09-03" and sid in(994,290) limit 3,10';
    //echo $sql . "\n";
    $start = microtime(true);
    //$parser = new EsParser($sql, true);
    $parser = new EsParser($sql, true,"http://127.0.0.1:9200");//第三个参数是es的http地址
    $stop = microtime(true);
    print_r($parser->result);//打印结果
    //print_r($parser->explain()); //打印dsl
### 目前支持的sql函数
    *  SQL Select
    *  SQL Delete
    *  SQL Where
    *  SQL Order By
    *  SQL Group By
    *  SQL AND 
    *  SQL Like
    *  SQL COUNT distinct
    *  SQL In
    *  SQL avg()
    *  SQL count()
    *  SQL max()
    *  SQL min()
    *  SQL sum()
### 使用注意事项
    该版本是基于elasticsearch5.x以上开发的，elasticsearch2.x及其以下不支持
### 交流使用
    qq群：578276199
### 项目地址
    github：https://github.com/qieangel2013/EsParser
    oschina：https://gitee.com/qieangel2013/EsParser/
