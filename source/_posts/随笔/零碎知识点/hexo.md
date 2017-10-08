.gitmodules
robots.txt



### _macro/post.swig

* 修改hexo/lib/plugins/processor/post.js
 var nowPath = data.source.substring(7);
      var nowCategory = nowPath.substring(0 , nowPath.indexOf('/'));
      data.categories = nowCategory;
      var post_s = data.source.substring(data.source.lastIndexOf('/') + 1) + '' ;
      var post_t = post_s.replace('.md','') ;
      var post_title = post_t.replace('.MD','') ;
      data.title = post_title;

      