# friendly-box2d.js
A friendlier version of box2d for JavaScript. FB2D wraps up the complexity of [box2dweb](http://code.google.com/p/box2dweb)
for easier use.

## Example     
```javascript      
var fps = 1/30,
    stepSize = 4,
    world;
    
world = new Box2D.world({
    drawRatio : $(window).width(),
    gravity : {
        x : 0,
        y : 9.8
    }
});

world.addBody({
    shape : 'circle',
    radius : '50px',
    friction : 0.1,
    id : '#circle'
});

setInterval(function() {
    world.step(1/fps, stepSize, stepSize);
    world.iterBodies(function(i, body) {
      if (body.id != undefined) {
          var pos = body.GetPosition(),
              angle = body.GetAngle(),
              obj = $(body.id);
                          
          obj.css('left', pos.x * world.drawRatio() - obj.width()/2 + 'px');
          obj.css('top', pos.y * world.drawRatio() - obj.height()/2 + 'px');
          // CSS rotation here
      }
    });
    world.clearForces();
});   
```

## License
Copyright (c) 2006-2007 Erin Catto http://www.gphysics.com

This software is provided 'as-is', without any express or implied
warranty.  In no event will the authors be held liable for any damages
arising from the use of this software.
Permission is granted to anyone to use this software for any purpose,
including commercial applications, and to alter it and redistribute it
freely, subject to the following restrictions:
1. The origin of this software must not be misrepresented; you must not
claim that you wrote the original software. If you use this software
in a product, an acknowledgment in the product documentation would be
appreciated but is not required.
2. Altered source versions must be plainly marked as such, and must not be
misrepresented as being the original software.
3. This notice may not be removed or altered from any source distribution.