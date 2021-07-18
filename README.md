# Base-conversion
%for MATLAB only
%Conversion between different numeric system
clearvars
clc
disp('Transformer v1.0 press "enter" to continue');
target = input ('Enter the number in Decimal');
target0 = target;
Level = input ('Please enter the target system (Only Binary is available yet)');
while Level ~= 2 && Level ~= 8 && Level ~= 16
    disp('Please enter again, this system is only available for binary,octal and hexadecimal ')
    Level = input('Please enter the target system (Only Binary is available yet)');
end
if Level == 2
    box = [];
    i = 0;
    quotient = 1;
    while quotient ~= 0
        remainder = mod(target,Level);
        quotient = (target - remainder)/Level;
        i = i + 1;
        box(1,i) = remainder;
        target = quotient;
    end
    j = 1;
    len = length(box);
    box0 = fliplr(box);
    result = 0;
    if mod(len,2) == 0
        while j <= len
            result = result + (box(1,j))*10^(j-1);
            j = j + 1;
        end
    else
        while j <= len
            result = result + (box(1,j))*10^(j-2);
            j = j + 1;
        end 
    end
    fprintf("%d in decimal corresponds to %d in binary", target0, result);
end
