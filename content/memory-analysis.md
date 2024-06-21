Title:  Test Page
Date: 2024-06-20
Category:  .Net
Tags: .net, memory, debugging, perfview, vs, sos, windbg
Author: Lee Culver
Summary:  Test summary

# Introduction

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Aliquet nibh praesent tristique magna sit amet purus. Dictum non consectetur a erat nam at lectus urna. Ullamcorper malesuada proin libero nunc consequat. Gravida rutrum quisque non tellus orci. Vel risus commodo viverra maecenas accumsan. Enim nunc faucibus a pellentesque sit amet. Magna ac placerat vestibulum lectus mauris ultrices eros. Vulputate mi sit amet mauris commodo quis. In fermentum et sollicitudin ac. Metus dictum at tempor commodo ullamcorper. Bibendum at varius vel pharetra vel turpis nunc eget. Sit amet consectetur adipiscing elit pellentesque habitant morbi. Id porta nibh venenatis cras sed. Quis vel eros donec ac odio tempor. Ut tortor pretium viverra suspendisse potenti nullam ac tortor.

Senectus et netus et malesuada fames. Velit ut tortor pretium viverra suspendisse potenti nullam ac tortor. Tortor at auctor urna nunc. Id leo in vitae turpis. Vestibulum morbi blandit cursus risus at. Faucibus nisl tincidunt eget nullam non nisi est sit amet. Interdum varius sit amet mattis. Et ligula ullamcorper malesuada proin. Ut placerat orci nulla pellentesque dignissim enim sit. Iaculis urna id volutpat lacus laoreet non. Tristique risus nec feugiat in fermentum posuere urna nec tincidunt. Convallis convallis tellus id interdum velit laoreet id donec. Bibendum enim facilisis gravida neque convallis a cras semper auctor. Mus mauris vitae ultricies leo integer malesuada.

In iaculis nunc sed augue lacus viverra vitae congue eu. Consequat interdum varius sit amet mattis vulputate enim nulla. Lobortis feugiat vivamus at augue eget arcu dictum. Odio euismod lacinia at quis risus. Sem viverra aliquet eget sit amet tellus cras adipiscing enim. Ipsum nunc aliquet bibendum enim. Morbi tristique senectus et netus et malesuada fames ac. Adipiscing elit pellentesque habitant morbi tristique senectus et netus et. Donec et odio pellentesque diam volutpat commodo sed egestas. Viverra ipsum nunc aliquet bibendum enim facilisis gravida neque. Massa vitae tortor condimentum lacinia quis. Dui nunc mattis enim ut tellus elementum sagittis vitae et. Lorem sed risus ultricies tristique nulla aliquet enim. In nibh mauris cursus mattis molestie. Condimentum mattis pellentesque id nibh tortor. Commodo sed egestas egestas fringilla phasellus faucibus scelerisque eleifend. Faucibus pulvinar elementum integer enim neque volutpat ac tincidunt. Malesuada fames ac turpis egestas sed tempus urna et. Nisi scelerisque eu ultrices vitae auctor eu augue. Eu facilisis sed odio morbi.

Egestas sed sed risus pretium quam vulputate. Ornare arcu odio ut sem nulla. Senectus et netus et malesuada fames ac. Eu sem integer vitae justo eget magna. Eu turpis egestas pretium aenean pharetra. Orci dapibus ultrices in iaculis nunc sed augue lacus. Nec tincidunt praesent semper feugiat nibh sed pulvinar proin gravida. Orci dapibus ultrices in iaculis nunc sed. Feugiat in fermentum posuere urna. Tristique magna sit amet purus gravida. Pellentesque dignissim enim sit amet.

Eget est lorem ipsum dolor sit amet. Quis auctor elit sed vulputate mi sit. Augue interdum velit euismod in. Sit amet risus nullam eget. Euismod lacinia at quis risus sed. Nibh cras pulvinar mattis nunc sed. Sodales neque sodales ut etiam sit amet nisl purus. Est placerat in egestas erat imperdiet sed euismod. Volutpat maecenas volutpat blandit aliquam etiam erat. Egestas fringilla phasellus faucibus scelerisque eleifend donec. Neque aliquam vestibulum morbi blandit cursus risus at ultrices. Ornare quam viverra orci sagittis eu volutpat odio. Nunc non blandit massa enim nec dui nunc. Mi sit amet mauris commodo quis. Mauris nunc congue nisi vitae suscipit tellus mauris a diam.


``` C#
        public override ClrObject Object
        {
            get
            {
                if (_object.Address != 0)
                    return _object;

                ClrObject obj = base.Object;
                if (obj.Type is not null)
                {
                    _object = obj;
                }
                else
                {
                    ClrObject prev = _heap.FindPreviousObjectOnSegment(obj);
                    if (prev.IsValid && prev <= obj && obj < prev + prev.Size)
                    {
                        _object = prev;
                    }
                    else
                    {
                        _object = obj;
                    }
                }

                return _object;
            }
        }
```