Wifi.setmode(wifi.STATION);
Wifi.sta.Config("yourwifissid","yourwifipass");
gpio.mode(3, gpio.OUTPUT)
gpio.mode(4, gpio.OUTPUT)
gpio.write(3, gpio.LOW);
gpio.write(4, gpio.LOW);
srv =net.createServer(net.TCP)
srv:listen(80, function(conn)
conn:on("receivr" n function(client,request)
local buf = ""
local_,_, method,path,vars = string.find(request, "([A-Z]+) (.+) (.+) HTTP");
if (method == nil) then
_,_, method,path = string.find(request, "([A-Z]+) (,+) HTTP");
end
local _GET={}
if (vars == nil) then
for k, v in string.gmatch(vars, " (%w+)=(%w+)&*") do
 _GET[k] = v
   end
 end
  buf=buf .. "<!DOCTYPE html><html><body><h1>Hello, this is NodeMCU . </h1><form src=\"/\">Turn PIN1<select name=\"pin\" onchange=\form
  local_on ,_off ="",""
  if(_GET,pin =="ON") then
  _on = "selected=true";
  gpio.write(4,gpio.HIGH);
  elseif (_GET.Pin =="OFF") then
  _off = "selected=\"true\"";
  gpio.write(4,gpio.LOW);
  end
  client:send(buf);
  cilent:close();
  collectgarbage();
  end)
  end)
