--car by color
select CarName , ColorName as car from dbo.car
inner join dbo.color 
on dbo.Color.ColorID=dbo.car.CarColorID_Color
 
select passengerfullname, tripcode,max(tripprice) as highprice from dbo.Passenger
left join 
dbo.trip on dbo.Passenger.PassengerCode=dbo.trip.PassengerCode_Passenger 
group by PassengerFullname,TripCode
having max(tripprice)>20000

select top 2 passengerfullname 
from dbo.Passenger

select PassengerCode_Passenger from dbo.trip
where tripprice = (select min(tripprice)from dbo.trip) and 
TripEndTime<11

select distinct PassengerCode_Passenger,sum(tripprice) as sumofprice
from dbo.Trip
group by PassengerCode_Passenger
order by sum(tripprice)

select Comment 
from dbo.Comment
where comment like '%trip%'

--union driver and passenger
select passengerfullname as fullname ,passengercode as code from dbo.Passenger
union
select driverfullname,drivercode from dbo.Driver

select carname, CarMake=
case
when carmakename='saipa' then 'cheap car'
when CarMakeName='bahman' then 'expensive car'
else 'normal'
end
from dbo.carmake inner join dbo.car on dbo.CarMake.CarMakeID=dbo.car.CarMakeID_CarMake

select PaymentTyeID,PaymentTypeName,paymenttypename=
case
when paymenttypename ='online' then 'fast'
when paymenttypename='naghdi' then 'in person'
end
from dbo.PaymentType 
 
select  DrivingLicenseID,year(DrivingLicenseExpiryDate) as expiryear
from dbo.DrivingLicense

select directionid,origin,Destination from dbo.direction
where origin!='saadatabad'

select * from dbo.Address
where len(address)<30
 
select distinct PassengerCode_Passenger,max(tripprice) as maxprice
from dbo.Trip
group by PassengerCode_Passenger
order by max(tripprice) desc

select * from dbo.trip
where TripPrice>(select avg(tripprice) from dbo.Trip)

