# 第四天

```javascript
$(document).ready(function() {
  var route = [];
  var daytime = '';
  var act = 1;
  $('a.btn_day').click(function() {
    daytime = '#day';
    $('#main').hide();
    $('#day').show();
    $(daytime + ' .scene1').show();
    $(daytime + ' #stage.act1').show();
    $(daytime + ' #stage.act1')[0].play();
  });
  $('a.btn_night').click(function() {
    daytime = '#night';
    $('#main').hide();
    $('#night').show();
    $(daytime + ' .scene1').show();
    $(daytime + ' #stage.act1').show();
    $(daytime + ' #stage.act1')[0].play();
  });
  $(daytime + ' a.btn_home').click(function() {
    $(daytime + ' .scene1').hide();
    $(daytime + ' .scene0').hide();
    $(daytime).hide();
    $('a.routed').each(function() {
      $(this).removeClass('routed').addClass('unroute');
    });
    route = [];
    act = 1;
    $('#main').show();
  });
  $(daytime + ' .scene1 a.btn_next').click(function() {
    $(daytime + ' #stage.act' + act)[0].pause();
    $(daytime + ' #stage.act' + act).hide();
    if (act == 1) {
      $(daytime + ' #stage.act2').show();
      $(daytime + ' #stage.act2')[0].play();
      act += 1;
    } else if (act == 6) {
      $(this).hide();
      if (route[0] == 'routeD' && route[1] == 'routeC' && route[2] == 'routeB' && route[3] == 'routeA') {1
        $(daytime + ' #stage.out1').show();
        $(daytime + ' #stage.out1')[0].play();
      } else {
        $(daytime + ' #stage.out2').show();
        $(daytime + ' #stage.out2')[0].play();
      }
    } else {
      $(daytime + ' .scene1').hide();
      $(daytime + ' .scene0').show();
    }
  });
  // Scene workflow
  $(daytime + ' .scene0 a.path').click(function() {
    route.push($(this).attr('id'));
    $(daytime + ' .scene0').hide();
    $(daytime + ' .scene1').show();
    $(this).removeClass('unroute').addClass('routed');
    act = route.length + 2;
    $(daytime + ' #stage.act'+act).show();
    $(daytime + ' #stage.act'+act)[0].play();
  });
  $(daytime + ' #stage.act').on('ended', function() {
    $(this).hide();
    $(daytime + ' .scene1').hide();
    $(daytime + ' .scene0').show();
  });
  // Reset all data when a scene finished
  $(daytime + ' #stage.out').on('ended', function() {
    $(this).hide();
    $(daytime + ' #stage').hide();
    $(daytime).hide();
    $('a.routed').each(function() {
      $(this).removeClass('routed').addClass('unroute');
    });
    route = [];
    act = 1;
    $('#main').show();
  });
  $(daytime + ' #stage.act1').on('ended', function() {
    $(this).hide();
    $(daytime + ' #stage.act2').show();
    $(daytime + ' #stage.act2')[0].play();
  });
  $(daytime + ' #stage.act6').on('ended', function() {
    $(this).hide();
    $(daytime + ' .scene1 a.btn_next').hide();
    if (route[0] == 'routeD' && route[1] == 'routeC' && route[2] == 'routeB' && route[3] == 'routeA') {
      $(daytime + ' #stage.out1').show();
      $(daytime + ' #stage.out1')[0].play();
    } else {
      $(daytime + ' #stage.out2').show();
      $(daytime + ' #stage.out2')[0].play();
    }
  });
});
```
