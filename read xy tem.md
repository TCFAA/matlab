
clc;
clear;
lon=ncread('TEM.nc','lon');%读取经度
lat=ncread('TEM.nc','lat');%读取纬度
air=ncread('air2016.nc','air');%读取气温
air1=permute(air,[2,1,3]);%第一第二维度转置
j=[]
for day=1:366
    air2=air1(27,45,day);
    j=[j,air2];
end
j=j-273.15;
m=mean(j);
m1=m*ones(1,366);
plot(m1,'LineWidth',2,'LineStyle','-.','Color',[1 0 0]);
hold on
plot(j);
grid off
title({'2016年逐日平均气温曲线';'地点：25N  110E'})
xlabel('day','FontSize',12)
ylabel('tem','FontSize',12)
set(gca,'xlim',[1 366]);
% set(gca,'xticklabel',1:1:12)

