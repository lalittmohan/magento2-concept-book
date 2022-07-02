## How is the selected shipping method's rate calculated?

[code]([magento/magento2/blob/2.2.3/app/code/Magento/Quote/Model/Quote/Address/Total/Shipping.php#L164-L182](https://github.com/magento/magento2/blob/2.2.3/app/code/Magento/Quote/Model/Quote/Address/Total/Shipping.php#L164-L182))

<!-- select:start -->
<!-- select-menu-labels: Magento Version -->
#### --2.2.3--
```
    if ($method) {
        foreach ($address->getAllShippingRates() as $rate) {
            if ($rate->getCode() == $method) {
                $store = $quote->getStore();
                $amountPrice = $this->priceCurrency->convert(
                    $rate->getPrice(),
                    $store
                );
                $total->setTotalAmount($this->getCode(), $amountPrice);
                $total->setBaseTotalAmount($this->getCode(), $rate->getPrice());
                $shippingDescription = $rate->getCarrierTitle() . ' - ' . $rate->getMethodTitle();
                $address->setShippingDescription(trim($shippingDescription, ' -'));
                $total->setBaseShippingAmount($rate->getPrice());
                $total->setShippingAmount($amountPrice);
                $total->setShippingDescription($address->getShippingDescription());
                break;
            }
        }
    }

```
#### --2.3--
#### --2.4--

<!-- select:end -->
