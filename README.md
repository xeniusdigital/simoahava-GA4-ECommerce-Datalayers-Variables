https://www.simoahava.com/analytics/google-analytics-4-ecommerce-guide-google-tag-manager/

# simoahava-GA4-ECommerce-Datalayers-Variables

##VIEW_PROMOTION
A view_promotion event is sent when the user sees one or more promotion items on the page. Promotions are a different data model from the rest of GA4 Ecommerce, as they do not necessarily involve products at all, but rather banners, campaigns, and such.

#Data Layer composition
A sample dataLayer object for the view_promotion event could look like this

window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'view_promotion',
  ecommerce: {
    items: [{
      promotion_id: 'sc2021',
      promotion_name: 'summer_campaign_2021',
      creative_name: 'family_in_bathing_suits_1',
      creative_slot: 'featured_items',
      location_id: 'hero_banner'
    },{
      promotion_id: 'wc2020',
      promotion_name: 'winter_campaign_2020',
      creative_name: 'family_in_winter_clothes_1',
      creative_slot: 'featured_items_2',
      location_id: 'hero_banner'
    }]
  }
});


##SELECT_PROMOTION
The select_promotion event is sent when the user clicks or selects one of the promotions they viewed.

#Data Layer composition
A sample dataLayer object for the select_promotion event could look like this (adapted from the official documentation):

window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  event: 'select_promotion',
  ecommerce: {
    items: [{
      promotion_id: 'sc2021',
      promotion_name: 'summer_campaign_2021',
      creative_name: 'family_in_bathing_suits_1',
      creative_slot: 'featured_items',
      location_id: 'hero_banner'
    }]
  }
});


Migration from Enhanced Ecommerce
If you want to use the Enhanced Ecommerce promotions array instead of creating a new items object, you need to create the following variable:

Type: Data Layer Variable
Data Layer Variable name: ecommerce.promoClick.promotions
Data Layer Version: Version 2
Then you can add it to your GA4 select_promotion event tag as the value of the items field (see the next chapter).

You can also use my custom variable template to convert an Enhanced Ecommerce promotions object automatically to the format required by select_promotion.











