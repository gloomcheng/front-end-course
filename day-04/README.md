# 第四天

+ [jQuery 實作練習](sample-01)

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
+ [Bootstrap 實作練習]

```html
    <!-- Carousel
    ================================================== -->
    <div id="myCarousel" class="carousel slide" data-ride="carousel">
      <!-- Indicators -->
      <ol class="carousel-indicators">
        <li data-target="#myCarousel" data-slide-to="0"
class="active"></li>
        <li data-target="#myCarousel" data-slide-to="1"></li>
        <li data-target="#myCarousel" data-slide-to="2"></li>
      </ol>
      <div class="carousel-inner" role="listbox">
        <div class="item active">
          <img class="first-slide"
src="data:image/gif;base64,R0lGODlhAQABAIAAAHd3dwAAACH5BAAAAAAALAAAAAABAAEAAAICRAEAOw=="
alt="First slide">
          <div class="container">
            <div class="carousel-caption">
              <h1>Example headline.</h1>
              <p>Note: If you're viewing this page via a
<code>file://</code> URL, the "next" and "previous" Glyphicon buttons on
the left and right might not load/display properly due to web browser
security rules.</p>
              <p><a class="btn btn-lg btn-primary" href="#"
role="button">Sign up today</a></p>
            </div>
          </div>
        </div>
        <div class="item">
          <img class="second-slide"
src="data:image/gif;base64,R0lGODlhAQABAIAAAHd3dwAAACH5BAAAAAAALAAAAAABAAEAAAICRAEAOw=="
alt="Second slide">
          <div class="container">
            <div class="carousel-caption">
              <h1>Another example headline.</h1>
              <p>Cras justo odio, dapibus ac facilisis in, egestas eget
quam. Donec id elit non mi porta gravida at eget metus. Nullam id dolor
id nibh ultricies vehicula ut id elit.</p>
              <p><a class="btn btn-lg btn-primary" href="#"
role="button">Learn more</a></p>
            </div>
          </div>
        </div>
        <div class="item">
          <img class="third-slide"
src="data:image/gif;base64,R0lGODlhAQABAIAAAHd3dwAAACH5BAAAAAAALAAAAAABAAEAAAICRAEAOw=="
alt="Third slide">
          <div class="container">
            <div class="carousel-caption">
              <h1>One more for good measure.</h1>
              <p>Cras justo odio, dapibus ac facilisis in, egestas eget
quam. Donec id elit non mi porta gravida at eget metus. Nullam id dolor
id nibh ultricies vehicula ut id elit.</p>
              <p><a class="btn btn-lg btn-primary" href="#"
role="button">Browse gallery</a></p>
            </div>
          </div>
        </div>
      </div>
      <a class="left carousel-control" href="#myCarousel" role="button"
data-slide="prev">
        <span class="glyphicon glyphicon-chevron-left"
aria-hidden="true"></span>
        <span class="sr-only">Previous</span>
      </a>
      <a class="right carousel-control" href="#myCarousel" role="button"
data-slide="next">
        <span class="glyphicon glyphicon-chevron-right"
aria-hidden="true"></span>
        <span class="sr-only">Next</span>
      </a>
    </div><!-- /.carousel -->
```
