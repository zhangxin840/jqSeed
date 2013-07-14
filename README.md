jqSeed
======

####jQuery plugin template

    
    /* Author: Zhang Xin */
    
    /* For jsHint */
    /* global jQuery: false*/
    /* jshint devel: true */
    
    ;(function($) {"use strict";
        var pluginName = 'restoreForm';
    
        var pluginController = function(element, theOptions) {
            var $container = $(element);
            var defaults = {
    
            };
    
            // Get options saved within $container's data attributes
            var meta = $container.data(pluginName + '-options');
            var options = $.extend(defaults, meta, theOptions);
    
            var init = function() {
    
            };
    
            // Destroy the warp object without removing elements
            var destroy = function() {
                // Unbind events
                $container.off('.' + pluginName);
                $container.find('*').off('.' + pluginName);
                // Remove data
                $container.removeData(pluginName);
                $container = null;
            };
    
            // Wapper object
            var that = {};
            that.options = options;
            that.destroy = destroy;
    
            // Initialize the wrapper object to generate elements of the widget
            init();
    
            //
            // Store wrapper object in $container using jQuery's $.data function.
            // Usage: console.log($('#theListener').data('jqListener'));
            $container.data(pluginName, that);
        };
    
        //
        // jQuery function
        //
        $.fn[pluginName] = function(options) {
            this.each(function() {
                pluginController(this, options);
            });
            // Chain-ability of jQuery objects
            return this;
        };
    })(jQuery);
